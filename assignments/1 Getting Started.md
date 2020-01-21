# Getting started

## Introduction

This assignment is all about getting to know the Atom development environment and to be able to run code on the pycom LoPy4 boards.

 * Install Atom and pymkr plugin
 * Connect LoPy4 to a computer
 * Connect to board in Atom and run code in console (on the hardware)
 * Upload files and run code on the microcontroller

## Rules
This task is going to be conducted in a group of two students. Both students must be active during all steps of the assignment.

During the assignment you may discuss the assignment with students outside the group. You may help other groups but you may NOT do all steps for them. Note that these rules change between assignments.

## Ingredients

### Hardware
 * One LOPY-4 board
 * One expansion board
 * One LoRa Antenna
 * One Micro-USB-Cable
 * One computer

### Software
 * Atom programming environment https://atom.io/
 * pymakr plugin https://atom.io/packages/pymakr

### Knowledge components
 * configure atom
 * run code in the REPL https://docs.micropython.org/en/latest/reference/repl.html
 * upload and run code in files
 * print() strings to console https://www.w3schools.com/python/ref_func_print.asp
 * import statements http://wiki.micropython.org/Importing-Modules
 * for-loops with range() https://www.w3schools.com/python/python_for_loops.asp
 * pycom.rgbled() https://docs.pycom.io/firmwareapi/pycom/pycom/
 * time.sleep() https://docs.pycom.io/firmwareapi/micropython/utime/



## Steps
Complete each step before progressing to the next.

### Step 1. Hardware setup

![Setup for Getting Started](/images/1_hardware.png)
* Connect the LoPy4 on the expansion board. Doublecheck the direction, the LED should be in the same direction as the micro-USB connection.
* Connect the Antenna to the Lopy 868MHz/915MHz (LoRa & Sigfox) antenna port. Be careful, and note there are three connectors. Check this: https://docs.pycom.io/gettingstarted/connection/lopy4/
* Connect the usb-cable to both computer and board

### Step 2. Software setup
 * Download and install Atom
 * Install pymakr plugin in Atom (using the package manager, settings Packages) 

### Step 3.
Make sure the LoPy board is connected to a computer with atom and pymkr installed.

When the board is properly setup you can run micropython code directly on it using the pymakr-console. The output from the commands are sent to the computer so that you can interact with the board. 

Write help() in the pycmkr console and press enter, this should give you output like in "Expected output 1"
```
>>>help()
```

The help command prints some useful short-cuts you can use to for example interrupt a board that is stuck in a loop so that you can upload new code. 

#### Expected output. Run help() on board
![Goal state 1](/images/1_goal_state_1.png)

### Step 4. Run custom code on the board
Create project folder in Atom, with a main.py file and run it. 

Using Atom, create a new file (main.py) with the following content but replace "Name 1" and "Name 2" with group members usernames
```
print("Hello, Name 1, Name 2!")
```
Press upload ![PyMkr Upload Button](/images/upload.png)

When the upload has completed the code willrun on the board and should produce the same output as in Expected output 2

#### Expected output 2. 
![Goal state 2](/images/1_goal_state_2.png)

### Step 5. Follow a tutorial and modify code, blink a light.
Use the built in RGB-LED-light to blink in different colors.

Read and complete this tutorial
https://docs.pycom.io/tutorials/all/rgbled/

Then rewrite the code so that the RGB-LED flashes in two second interval but also prints the name of the color(red, green, yellow) to the console.

### Expected output 3. :

 * The color of the built-in LED on the LOPY4 board switches between red, green, yellow ever second.
 * The color-name is also written on the console at the same time.

```Red
Green
Yellow
Red
Green
Yellow
Red
```

## Examination
When you have completed this assignment you are expected to know:
 * How to setup a pycom-development environment with Atom and the pymakr plugin.
 * How to run python commands using the console.
 * How to upload and run code in files using pymakr
 * How to blink the built in LED

This task is examined using self-examination. Make sure all students in your group understands every step before you proceed.


