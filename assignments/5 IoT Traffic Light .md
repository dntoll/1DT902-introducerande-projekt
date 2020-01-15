# The Traffic Light

## Goals
To synchronize with cloud using mqtt

## Rules

This task is going to be conducted in a group of two students. Both students must be active during all steps of the assignment.

During the assignment you may discuss the assignment with students outside the group. 
You may help other groups but you may NOT do all steps for them, or share any code. Note that these rules change between assignments.

## Knowledge Components

 * mqtt https://en.wikipedia.org/wiki/MQTT
 

## Ingredients

### Hardware
 One traffic light component.
 
 
 
## Steps

### Step 1. Get an Adafruit IO account
### Step 2. Simple communication from pycom over WLAN
To be able to communicate to io.adafruit.com we need a WiFi connection. Simplest is to share network from phone or use a guest network.

'''
from network import WLAN
wlan = WLAN(mode=WLAN.STA)
wlan.connect("wifi_network_id", auth=(WLAN.WPA2, "SecretPassword"), timeout=5000)
while not wlan.isconnected():
    machine.idle()
print("Connected to WiFi\n")
'''

### Step 3. Communicating trafficlight
### Step 4. Syncing trafficlights
 
 

 
 
 
