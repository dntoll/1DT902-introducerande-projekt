# Blink External LED's

## Goals

## Rules

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
 * Light Emitting Diode's (LED's) https://en.wikipedia.org/wiki/Light-emitting_diode
 * Resistors (motstånd)
 * Basic LED circuit https://en.wikipedia.org/wiki/LED_circuit
 * Microcontroller GPIO
 * LOPY4 Datasheet https://docs.pycom.io/gitbook/assets/specsheets/Pycom_002_Specsheets_LoPy4_v2.pdf 

## Hardware setup

 * Disconnect the USB cable. When changing components on the breadboard, always have the USB disconnected!
 * Connect the GND to the black power rail and 3V3 to the red power rails of the breadboard (See breadboard tutorial if needed)
 * Connect the three LED circuits as in this video https://www.youtube.com/watch?v=yQ2-yVXFMeE but use the power rails as + and - of the battery and use a 560 Ohm resistor. 
 * Make sure each LED lights up when you connect the USB-cable. 
 
## Software setup
 * Atom with pymakr plugin

## Steps

### Conntect 
IMPORTANT: We are now going to connect external LED's to the microcontroller. The LOPY 4 microcontroller provides General Purpose Input Output (GPIO)-ports that can be used to communicate with external components. The ports are a bit sensitive and should not be used to directly drive heavy loads (like a motor).

The Datasheet for LOPY4 says "Absolute MAX per pin 12mA, recommended 6mA" which means we must reduce current. If more current is needed, additional components (eg. transistors, or drivers) can be used. Thankfully our scenario does not require much current and we can reduce the current flow by having a 560 Ohm resistor in series with each LED we connect.

 * Disconnect the USB cable again
 * Remove the wire going into the red power rail but keep the GND cable.
 * Replace the wires going into the anode of the LED from the red (3V3) power rail with a cable going into port P8 to p10 of the LOPY4.
 * Run the following code

    from machine import Pin
    redLED = Pin("P8", mode=Pin.OUT)
    redLED.value(1)




## Examination

[![](http://img.youtube.com/vi/Wtd8pp-DW3w/0.jpg)](http://www.youtube.com/watch?v=Wtd8pp-DW3w "")
