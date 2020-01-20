# The Traffic Light

## Goals
To work with more code and more components. To apply the things we have learned so far.

## Rules

This task is going to be conducted in a group of two students. Both students must be active during all steps of the assignment.

During the assignment you may discuss the assignment with students outside the group. 
You may help other groups but you may NOT do all steps for them, or share any code. Note that these rules change between assignments.

## Knowledge Components
 * Apply knowledge components from previous assignments. 

## Ingredients

### Hardware
 * Six LED's with resistors (2 x Red, 2 x yellow, 2 x green)
 * Buzzer with resistor
 * Button with resistor
 
 
## Steps


### Step 1. Build Check all components

We are going to build a traffic light that can sit next to a pedestrian crossing. Thus it has three LEDs for traffic, two LED's for the pedestrian crossing and also a button circuit used by pedestrians to ask for green light. 

Individually build one circuit at a time and test those before continuing with the next
* a traffic light (Red, yellow, green - LED's), 
* a pedestrian crossing light (Red, Green LED) and a buzzer
* a pedestrian button (button circuit and yellow light that turns on when button has been pressed and waitng for )

When all hardware is set-up, write a routine that waits for a button press, then lights up each LED, and finally beeps the buzzer before waiting again.

### Step 2. Traffic light with pedestrian crossing

We are now going to model a pedestrian crossing light with python code. The traffic light is normally green.
The button should represent a pedestrian wanting to cross the street, when pressed the yellow button LED should light up and traffic should halt and pedestrians should be allowed passage before the traffic light turns green again.

We can model this by defining different states, each defined in its own function:

#### States:
 * TRAFFIC GO: Traffic Green LED, Pedestrian Red LED, Minimum 4 seconds but continue longer if not interrupted
 * TRAFFIC SOON STOP: Traffic Yellow LED, Pedestrian Red LED, 2 seconds
 * ALL STOP: Traffic Red LED, Pedestrian Red LED, 1 second
 * PEDESTRIAN GO: Traffic Red LED, Pedestrian Green LED, Buzzer speedy Tick sounds, 3 seconds
 * PEDESTRIAN SOON STOP: Traffic Red LED, Pedestrian Green LED, Slower Tick Sounds, 1 second
 * TRAFFIC GET READY: Traffic Green LED + Yellow LED, Pedestrian Red LED, 1 second
  
You can now write a main loop that normally runs the TRAFFIC GO state if nothing happens. If the button is pressed a boolean variable is set (you need a buttonEventCallback-function) and the main loops starts calling the different state-methods in order before.


### Examination

The traffic light should work like described above and go back to green after having stepped through all the states. The exact waiting time is not as important as each of the states being reached and this should be repeatable.

#### Check code
 * The code should follow Flake8 code standard ( however lines may be longer than 79 characters )
 * Code should be DRY ( no unnecessary repeated statements )
 * Code should be divided into methods
 * Method names should represent the content (for example state names)
 
 
 
 
 
