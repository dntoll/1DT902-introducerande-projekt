# Getting started

## Introduction

## Goals
 * Connect hardware 
 * Install Atom and pymkr plugin
 * Connect to board in Atom and run code in console (on the hardware)
 * Upload files and run code on the microcontroller

## Rules
This task is going to be conducted in a group of two students. 
During the assignment you may discuss the assignment with students outside the group. 
You may help other groups but you may NOT do all steps for them.
Note that these rules change between assignments.

The assingment is done when you have show

The deadline is ... 

## Ingredients

 * One LOPY-4 board
 * One expansion board
 * One LoRa Antenna
 * One Micro-USB-Cable
 * One computer
 * Atom programming environment https://atom.io/
  * Pymkr plugin https://atom.io/packages/pymakr

## Hardware setup

![Setup for Getting Started](/images/1_hardware.png)

* Connect the LOPY to the expansion board (doublecheck the direction)
* Connect the Antenna to the Lopy 866 antenna port (be careful, and note there are three connectors)
* Connect the usb-cable to both computer and board

## Software setup
 * Download and install Atom

## Steps

### Step 1
Make sure the LoPy board is connected to a computer with atom and pymkr installed.

Write help() in the pycmkr console, this should give you output like in "goal state 1

#### Expected output 1. Run help on board
![Goal state 1](/images/1_goal_state_1.png)

### Step 2. Run custom code on the board
Create project folder in Atom, with a main.py file and run it. 

Create a new file (main.py) with the following content but replace "Name 1" and "Name 2" with group members usernames
```
print("Hello, Name 1, Name 2!")
```
Press upload ![PyMkr Upload Button](/images/upload.png)

#### Expected output 2. 
![Goal state 2](/images/1_goal_state_2.png)

### Step 3. Follow a tutorial and modify code, blink a light.
Use the built in RGB-LED-light to blink in different colors.

Read and complete this tutorial
https://docs.pycom.io/tutorials/all/rgbled/

Then rewrite the code so that the RGB-LED flashes in two second interval but also prints the name of the color(red, green, yellow) to the console.

### Expected output 3. :

 * The color of the built-in LED switches between red, green, yellow ever second.
 * The color-name is also written on the console at the same time.

```Red
Green
Yellow
Red
Green
Yellow
Red```

## Examination

This examination can be done by your group themselves, you have completed the assignment your output is similar to the goal images above.

