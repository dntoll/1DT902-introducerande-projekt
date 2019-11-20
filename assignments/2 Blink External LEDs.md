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
 * Basic circuit
 * Microcontroller GPIO
 

## Hardware setup



[![](http://img.youtube.com/vi/Wtd8pp-DW3w/0.jpg)](http://www.youtube.com/watch?v=Wtd8pp-DW3w "")

We are going to connect external LED's to the microcontroller. The LOPY 4 microcontroller provides General Purpose Input Output (GPIO)-ports that can be used to communicate with external components. The ports are a bit sensitive and should not be used to directly drive heavy loads (like a motor). The Datasheet for LOPY4 says "Absolute MAX per pin 12mA, recommended 6mA" which means we must reduce current. If more current is needed, additional components (eg. transistors, or drivers) can be used. Thankfully our scenario does not require much current and we can reduce the current flow by having a 560 Ohm resistor in series with each LED we connect.

GND -> Minus rail on breadboard


## Software setup

## Steps




## Examination
