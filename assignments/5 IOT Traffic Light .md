# The Traffic Light

## Goals
To synchronize with cloud using mqtt

## Rules

This task is going to be conducted in a group of two students. Both students must be active during all steps of the assignment.

During the assignment you may discuss the assignment with students outside the group. 
You may help other groups but you may NOT do all steps for them, or share any code. Note that these rules change between assignments.

## Knowledge Components

 * mqtt wikipedia https://en.wikipedia.org/wiki/MQTT
 * mqtt pycom https://docs.pycom.io/tutorials/all/mqtt/
 

## Ingredients

### Hardware
 One traffic light component.
 
 
 
## Steps


### Step 1. Simple communication from pycom over WLAN
To be able to communicate to io.adafruit.com we need a WiFi connection. Simplest is to share network from phone or use a guest network.

Replace WIFI_NETWORK_ID with the sid of your network and YOUR_WIFI_PASSWORD with the passkey in the following code and make sure you can connect to your WIFI before continuing. 

```python
from network import WLAN
wlan = WLAN(mode=WLAN.STA)
wlan.connect("WIFI_NETWORK_ID", auth=(WLAN.WPA2, "YOUR_WIFI_PASSWORD"), timeout=5000)
while not wlan.isconnected():
    machine.idle()
print("Connected to WiFi\n")
```

### Step 2. Get an Adafruit IO account

ADAFRUIT_USER_NAME = 

### Step 3. Communicating trafficlight

Now its time to communicate using a mqtt-library to adafruit.io through the WiFi network. 

* Get the YOUR_AIO_KEY from https://io.adafruit.com/, click on "AIO Key"
* Create a feed:  https://io.adafruit.com/ADAFRUIT_USER_NAME/feeds
* Create a dashboard:  https://io.adafruit.com/ADAFRUIT_USER_NAME/dashboards/pycom
 * Add a simple Toggle item to the dashboard that you connect to your feed.
* Import the mqtt library (just upload the mqtt.py file ) ../lib/mqtt.py

The following 

```python
def sub_cb(topic, msg):
   print(msg)
   
client = MQTTClient("device_id", "io.adafruit.com",user="ADAFRUIT_USER_NAME", password="YOUR_AIO_KEY", port=1883)

client.set_callback(sub_cb)
client.connect()
client.subscribe(topic="ADAFRUIT_USER_NAME/feeds/myfeed")

while True:
    print("Sending ON")
    client.publish(topic="ADAFRUIT_USER_NAME/feeds/myfeed", msg="ON")
    time.sleep(1)
    print("Sending OFF")
    client.publish(topic="ADAFRUIT_USER_NAME/feeds/myfeed", msg="OFF")
    client.check_msg()
    time.sleep(1)
```

### Step 4. Syncing trafficlights
 
 

 
 
 
