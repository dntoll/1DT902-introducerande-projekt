# Blink External LED's

## Goals
To connect basic circuits.
To get LED-lights to blink.
To work with GPIO ports and loops.

## Rules

This task is going to be conducted in a group of two students. Both students must be active during all steps of the assignment.

During the assignment you may discuss the assignment with students outside the group. You may help other groups but you may NOT do all steps for them. Note that these rules change between assignments.

## Ingredients

### Hardware
 * Everything from task 1.
 * breadboard
 * 1 Red LED
 * 1 Yellow LED
 * 1 Green LED
 * 3 Resistors 560 Ohm (Green, Blue, Brown, Gold) or higher
 
### Software 
 * Everything from task 1.

### Knowledge components
 * Breadboards (kopplingsdäck) https://learn.sparkfun.com/tutorials/how-to-use-a-breadboard/all
 * Basic LED circuit https://en.wikipedia.org/wiki/LED_circuit
  * Light Emitting Diode's (LED's) https://en.wikipedia.org/wiki/Light-emitting_diode
  * Resistors (motstånd) https://en.wikipedia.org/wiki/Resistor
 * Microcontroller GPIO https://en.wikipedia.org/wiki/General-purpose_input/output
  * LOPY4 Datasheet https://docs.pycom.io/gitbook/assets/specsheets/Pycom_002_Specsheets_LoPy4_v2.pdf 
  * Make a GPIO port an output https://docs.pycom.io/firmwareapi/pycom/machine/pin/
  * Turn GPIO output on and off pin.value([value])
 * Make the thread sleep for a second  time.sleep(seconds)
 * Loops 

## Hardware setup

 * Disconnect the USB cable. When changing components on the breadboard, always have the USB disconnected!
 * Connect the GND to the black power rail and 3V3 to the red power rails of the breadboard (See breadboard tutorial if needed)
 * Connect the three LED circuits as in this video https://www.youtube.com/watch?v=yQ2-yVXFMeE but use the power rails as + and - of the battery and use a 560 Ohm resistor. 
 * Make sure each LED lights up when you connect the USB-cable. 
 
### Components 
 * LOPY4 GND <--> Black power rail (BPR)
 * LOPY4 3V3 <--> Red power rail (RPR)
 * RPR <--> [ Anode - LED - Cathode ] <--> [ 560 Ohm resistor ] <--> RPR
 
 ![LED Circuit, Wikipedia](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c9/LED_circuit.svg/1200px-LED_circuit.svg.png)
 
## Software setup
 * Atom with pymakr plugin

## Steps

### Driving LED with GPIO  
IMPORTANT: We are now going to connect external LED's to the microcontroller. The LOPY 4 microcontroller provides General Purpose Input Output (GPIO)-ports that can be used to communicate with external components. The ports are a bit sensitive and should not be used to directly drive heavy loads (like a motor).

The Datasheet for LOPY4 says "Absolute MAX per pin 12mA, recommended 6mA" which means we must reduce current. If more current is needed, additional components (eg. transistors, or drivers) can be used. Thankfully our scenario does not require much current and we can reduce the current flow by having a 560 Ohm resistor in series with each LED we connect.

 * Disconnect the USB cable again
 * Remove the wire going into the red power rail but keep the GND cable.
 * Replace the wires going into the anode of the LED from the red (3V3) power rail with a cable going from the LED anode to port P8 to p10 of the LOPY4.
 * Upload the following code in the main.py file

```python
import time
from machine import Pin
redLED = Pin("P8", mode=Pin.OUT) #Make GPIO P8 an output
redLED.value(1) # Send a 1 to GPIO to turn the LED on
time.sleep(1) # Sleep for a second
redLED.value(0) # Send a 0 to the GPIO to turn the LED off
```

### Components 
 * LOPY4 GND <--> Black power rail (BPR)
 * LOPY4 P8 <--> [ Anode - Red LED - Cathode ] <--> [ 560 Ohm resistor ] <--> RPR
 * LOPY4 P9 <--> [ Anode - Yellow LED - Cathode ] <--> [ 560 Ohm resistor ] <--> RPR
 * LOPY4 P10 <--> [ Anode - Green LED - Cathode ] <--> [ 560 Ohm resistor ] <--> RPR

#### Expected output

The Red LED lights up after the LOPY4 has booted, is on for one second and then turns off. The behaviour is repeated if the board is resetted.

### Driving multiple LED's with GPIO

Now adjust the code so that the three LED's blink as in the following:
 * RED lights up for 1 s. Other LEDs are unlit.
 * GREEN lights up for 1 s. Other LEDs are unlit.
 * YELLOW lights up for 1 s. Other LEDs are unlit.
 * Repeat forever with RED again

#### Expected output
[![](http://img.youtube.com/vi/Wtd8pp-DW3w/0.jpg)](http://www.youtube.com/watch?v=Wtd8pp-DW3w "")

## Examination
This task can be self-examined. When the LED's blink in the expected sequence you are done with the programming task.

Check yourself so that you know the answers to the following questions.
 * Which leg of the LED is longer, the cathode or the anode?
 * Why do we need a resistor?
 * How can we make the LED's blink faster?
 * Where can you find information about the different hardware limits in the LOPY4 board?
 * What are the components of a basic LED-circuit and how do we connect them in order for the LED to light up?


