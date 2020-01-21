# Blink External LED's

In this assignment we are going to work with user-input through a button circuit and also introduce a new form of output (sound). 

 * Work with input
 * Work with sound

## Rules

This task is going to be conducted in a group of two students. Both students must be active during all steps of the assignment.

During the assignment you may discuss the assignment with students outside the group. You may help other groups but you may NOT do all steps for them, or share any code. Note that these rules change between assignments.

## Knowledge Components
 * Buzzers (Svenska: Summer) https://en.wikipedia.org/wiki/Buzzer
    * Buzzer circuit https://www.instructables.com/id/How-to-use-a-Buzzer-Arduino-Tutorial/
    * Creating a PWM object https://docs.pycom.io/firmwareapi/pycom/machine/pwm/
    * Setting the duty cycle of the channel https://docs.pycom.io/firmwareapi/pycom/machine/pwm/
 * Button https://learn.sparkfun.com/tutorials/switch-basics/all
    * Button circuit with pull-down resistor https://learn.sparkfun.com/tutorials/pull-up-resistors
    * Defining callback function on events https://docs.pycom.io/firmwareapi/pycom/machine/pin/
    * Interrupts https://en.wikipedia.org/wiki/Interrupt
    * Taking a utime.ticks_ms() https://docs.pycom.io/firmwareapi/micropython/utime/
    * Contact Bounce https://www.allaboutcircuits.com/textbook/digital/chpt-4/contact-bounce/
 * Code
    * API: Reading time in ms. utime.ticks_ms()
    * event callback functions https://docs.pycom.io/firmwareapi/pycom/machine/pin/
    * global variables. https://www.programiz.com/python-programming/global-local-nonlocal-variables
    * API: Create PWM timer PWM(0, frequency=i)
    * timer duty cycle: duty_cycle(0.5) https://en.wikipedia.org/wiki/Duty_cycle
    * API: Make the microcontroller sleep. time.sleep()
    * declare function
  

## Ingredients

### Hardware
 * Everything from task 2. (3 LED with resistors)
 * Button 
 * pull-down resistor 1k Ohm (Brown, Black, Red, Gold)
 * Buzzer 
 * Buzzer-resistor 1k Ohm (Brown, Black, Red, Gold) 
 
### Software 
 * Everything from task 2.
 

## Steps

### Breadboard circuit
Connect the breadboard power-rails to GND and 3V3.

 * LOPY4 GND <--> Black Power Rail (BPR)
 * LOPY4 3V3 <--> Red Power Rail (RPR)
 
### The buzzer circuit
The buzzer is driven directly from the LOPY4 port but using a current reducing resistor. For higher volume it is adviceable to use a driver circuit.

Place the buzzer with one leg on each side of the breadboard ravine. Connect one side to the microcontroller port and the other through a resistor to GND. 

 * LOPY4 P6 <--> Buzzer <--> 1k Ohm resistor <--> BPR(GND)
 
### The button circuit
The button has two sides with two legs each (We call them A and B) that are connected when the button is pressed. The button is placed over the breadboard ravine. We connect the A-side to the input port of the microcontroller. We also connect the A side through a 1k Ohm resistor to GND, this pulls the input port voltage down to GND. GND counts as a LOW (or 0) when we read the input of the port through our code. The resistor is called a "pull-down resistor". We connect the B side of the button to 3v3. 

When the button is pressed the A and B-sides become connected the input becomes a HIGH (or 1) since we measure on the side now directly connected to 3v3. Please note that a current now runs through the 1kOhm connector. 

  * LOPY4 P11 <--> Button side A <--> 1k Ohm resistor <--> BPR(GND)
  * Button side B <--> RPR(3v3)
  
![Pull down button circuit](/images/pull-down-button.jpg)

### Step 1. Button with contact bounce-reduction

Run the following code with a button circuit on P11:
```
from machine import Pin

count = 0


def buttonEventCallback(argument):
    global count
    print("button was pressed: " + str(count))
    count += 1


buttonPin = Pin('P11', mode=Pin.IN, pull=None)
buttonPin.callback(Pin.IRQ_FALLING, buttonEventCallback)
```

Press the button a couple of times. Note that not all presses results in a single event being launched. Due to *contact bounces* we might end up with multiple button-presses even if the button was only pressed once.
Contact bounces are explained here: https://www.allaboutcircuits.com/textbook/digital/chpt-4/contact-bounce/

Rewrite the code so that at most one button press can happen each second. 
 * Use a variable to store the last time the button was pressed using utime.ticks_ms(). 
 * Ignore key-presses if the time since last press was less than a second.

The program output should look like the following when quickly pressing the button:
```
...
Button was pressed: 3 time(s). Time since last 1462ms
Button was pressed: 4 time(s). Time since last 1795ms
Button was pressed: 5 time(s). Time since last 1021ms
Ignored button press: Time left for next press is 809ms
Ignored button press: Time left for next press is 431ms
Button was pressed: 6 time(s). Time since last 1164ms
Ignored button press: Time left for next press is 789ms
Ignored button press: Time left for next press is 480ms
Ignored button press: Time left for next press is 475ms
Ignored button press: Time left for next press is 320ms
Ignored button press: Time left for next press is 261ms
Ignored button press: Time left for next press is 256ms
Ignored button press: Time left for next press is 184ms
Ignored button press: Time left for next press is 127ms
Button was pressed: 7 time(s). Time since last 2711ms
```


### Step 2. Press play for music

The following code is from https://forum.pycom.io/topic/802/example-pwm-mariobros

Rewrite the code so that the music is started when the button is pressed. Merge with code from step 1 so that button can still be pressed.
 * The playing of the tune should not be run in the event handler. The event handler interrupts the currently running code on the microcontroller and thus locks up the execution until its done. To many interrupts may cause the microcontroller to be unresponsive. 
 * Keypresses that happen during the playing of the tune should not result in cued up plays. 
 * You may reduce the length of the Tune, but it must be longer than the time for contact bounce. 


```

from machine import Pin
from machine import PWM
import time

# define frequency for each tone
E7 = 2637
F7 = 2794
C7 = 2093
G7 = 3136
G6 = 1568
E6 = 1319
A6 = 1760
B6 = 1976
AS6 = 1865
A7 = 3520
D7 = 2349

# set up pin PWM timer for output to buzzer or speaker
p2 = Pin("P7")  # Pin Y2 with timer 8 Channel 2
tim = PWM(0, frequency=300)
ch = tim.channel(2, duty_cycle=0.5, pin=p2)https://forum.pycom.io/topic/802/example-pwm-mariobros

mario = [E7, E7, 0, E7, 0, C7, E7, 0, G7, 0, 0, 0, G6, 0, 0, 0, C7, 0, 0, G6, 0, 0, E6, 0, 0, A6, 0, B6, 0, AS6, A6, 0, G6, E7, 0, G7, A7, 0, F7, G7, 0, E7, 0,C7, D7, B6, 0, 0, C7, 0, 0, G6, 0, 0, E6, 0, 0, A6, 0, B6, 0, AS6, A6, 0, G6, E7, 0, G7, A7, 0, F7, G7, 0, E7, 0,C7, D7, B6, 0, 0]

for i in mario:
    if i == 0:
        ch.duty_cycle(0)
    else:
        tim = PWM(0, frequency=i)
        ch.duty_cycle(0.5)

    time.sleep(0.15)
```

## Step 3. Blinky lights to tune. (Optional for extra credit/fun)

Assign one LED for each tone (multiple tones can be attached to the same LED ) turn on LED's in tune with the music.


## Examination

This assignment should be examined by a TA. Prepare for that by checking yourself so that you know the answers to the following questions.
 * What is the difference between a pull-up and a pull-down button circuit?
 * What is contact bounceing and why would we be bothered?
 * What is a microcontroller interrupt?
 * Why should we keep the code in event-callbacks to a minimum?
 * How can the song continue while the event-callback prints out key-presses?

When completed you should ask a TA to check your setup and ask you the questions above.

### Test setup:
 * The time for key-presses should be printed as the example in Step 2. 
 * Test by "spamming" the button with lots of short presses. The song should start on the first press and continue without interruption or repeated plays. The printouts of times should continue while the song is played.
 * If lights blink in tune with music, make extra credit note. 
 
### Check Code:
 * The code should follow Flake8 code standard ( however lines may be longer than 79 characters )
 * Code should be DRY ( no unnecessary repeated statements )
 * Code should be divided into methods
 * The song should not be played in the eventhandler-function but started in a separate loop (or thread).
 
### Check knowledge: 
 * Ask the group members individually two questions each of the above questions.


  
