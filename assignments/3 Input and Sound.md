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
The button has two sides (We call them A and B) that are connected when the button is pressed. The button is placed over the breadboard ravine. We connect the A-side to the input port of the microcontroller. We also connect the A side through a 1k Ohm resistor to GND, this pulls the input port voltage down to GND which counts as a LOW (or 0)  when we read the input of the port through our code. The resistor is called a "pull-down resistor". We connect the B side of the button to 3v3. 

When the button is pressed the A and B-sides become connected the input becomes a HIGH (or 1) since we measure on the side now directly connected to 3v3. Please note that a current now runs through the 1kOhm connector. 

![Button m.nu](https://images.m.nu/data/product/1000w/T1ls6WXfFaXXXCF87Y_030446.jpg)

  * LOPY4 P11 <--> Button side A <--> 1k Ohm resistor <--> BPR(GND)
  * Button side B <--> RPR(3v3)

## Steps

### Step 1. Play a tune



  
  
