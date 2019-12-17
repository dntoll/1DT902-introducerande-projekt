# Blink External LED's

## Goals
To work with input
To work with sound

## Rules

This task is going to be conducted in a group of two students. Both students must be active during all steps of the assignment.

During the assignment you may discuss the assignment with students outside the group. You may help other groups but you may NOT do all steps for them. Note that these rules change between assignments.

## Knowledge Components
 * Buzzers (Svenska: Summer) https://en.wikipedia.org/wiki/Buzzer
    * Buzzer circuit
    * Creating a PWM object
    * Setting the duty cycle of the channel
 * Button 
    * Button circuit with pull-down resistor
    * Defining callback function on events 

## Ingredients

### Hardware
 * Everything from task 2. (3 LED with resistors)
 * Button 
 * pull-down resistor 1k Ohm (Brown, Black, Red, Gold)
 * Buzzer 
 * Buzzer-resistor 1k Ohm (Brown, Black, Red, Gold) 
 
### Software 
 * Everything from task 2.
 
## Hardware setup

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

## Steps

### Step 1. Press counter

Code for a button event:
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

Press the button a couple of times. Note that not all presses results in a single event being launched. 

### Step 2. Press play for music

The following code is from https://forum.pycom.io/topic/802/example-pwm-mariobros
```

from machine import Pin
from machine import PWM
import time

# define frequency for each tone
B0  = 31
C1  = 33
CS1 = 35
D1  = 37
DS1 = 39
E1  = 41
F1  = 44
FS1 = 46
G1  = 49
GS1 = 52
A1  = 55
AS1 = 58
B1  = 62
C2  = 65
CS2 = 69
D2  = 73
DS2 = 78
E2  = 82
F2  = 87
FS2 = 93
G2  = 98
GS2 = 104
A2  = 110
AS2 = 117
B2  = 123
C3  = 131
CS3 = 139
D3  = 147
DS3 = 156
E3  = 165
F3  = 175
FS3 = 185
G3  = 196
GS3 = 208
A3  = 220
AS3 = 233
B3  = 247
C4  = 262
CS4 = 277
D4  = 294
DS4 = 311
E4  = 330
F4  = 349
FS4 = 370
G4  = 392
GS4 = 415
A4  = 440
AS4 = 466
B4  = 494
C5  = 523
CS5 = 554
D5  = 587
DS5 = 622
E5  = 659
F5  = 698
FS5 = 740
G5  = 784
GS5 = 831
A5  = 880
AS5 = 932
B5  = 988
C6  = 1047
CS6 = 1109
D6  = 1175
DS6 = 1245
E6  = 1319
F6  = 1397
FS6 = 1480
G6  = 1568
GS6 = 1661
A6  = 1760
AS6 = 1865
B6  = 1976
C7  = 2093
CS7 = 2217
D7  = 2349
DS7 = 2489
E7  = 2637
F7  = 2794
FS7 = 2960
G7  = 3136
GS7 = 3322
A7  = 3520
AS7 = 3729
B7  = 3951
C8  = 4186
CS8 = 4435
D8  = 4699
DS8 = 4978

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



  
  
