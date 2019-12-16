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
The buzzer is driven directly from the LOPY4 port but using a current reducing resistor. 
 * LOPY4 P6 <--> Buzzer <--> 1k Ohm resistor <--> BPR(GND)
 
### The button circuit
The button has two sides (A and B) that are connected when the button is pressed. 
[Button m.nu](https://images.m.nu/data/product/1000w/T1ls6WXfFaXXXCF87Y_030446.jpg)
  * LOPY4 P11 <--> Button side A <--> 1k Ohm resistor <--> RPR(3v3)
  * Button side B <--> RPR(3v3)

## Steps

### Step 1. Play a tune



  
  
