# The IOT Traffic Light

The previous tasks has been a single LoPy4 device on its own without any communication. In this final assignment we connect our LoPy4 to internet over WiFi and push information to an online server. 

 * Simple Internet Of Things (IoT) scenario
 * Connect Lopy4 by wifi. 
 * Synchronize with cloud using mqtt
 

## Rules

This task is going to be conducted in a group of two students. Both students must be active during all steps of the assignment.

During the assignment you may discuss the assignment with students outside the group. 
You may help other groups but you may NOT do all steps for them, or share any code. Note that these rules change between assignments.

## Knowledge Components

 * mqtt wikipedia https://en.wikipedia.org/wiki/MQTT
 * mqtt pycom https://docs.pycom.io/tutorials/all/mqtt/
 

## Ingredients

### Hardware
 One LoPy4 unit.
 
## Steps

### Step 1. Simple communication from pycom over WLAN
To be able to communicate to io.adafruit.com we need a WiFi connection. There is very little data sent so easiest is to share network from a smartphone, or use a guest WiFi-network.

Replace WIFI_NETWORK_ID with the sid of your network and YOUR_WIFI_PASSWORD with the passkey in the following code and make sure you can connect to your WIFI before continuing. 

```python
from network import WLAN
wlan = WLAN(mode=WLAN.STA)
wlan.connect("WIFI_NETWORK_ID", auth=(WLAN.WPA2, "YOUR_WIFI_PASSWORD"), timeout=5000)
while not wlan.isconnected():
    machine.idle()
print("Connected to WiFi")
```

The above scrips should eventually connect, not very fast to WiFi and show "Connected to WiFi".


### Step 2. Get an Adafruit IO account

Go to https://io.adafruit.com/  and sign up for a free account. Make note of your ADAFRUIT_USER_NAME since we need to use it in the following. When logged in, get the YOUR_AIO_KEY from https://io.adafruit.com/, click on "AIO Key"

 * ADAFRUIT_USER_NAME
 * YOUR_AIO_KEY


Note that you get the following in a free account.

 * 30 data points per minute
 * 30 days of data storage
 * 10 feeds
 * 5 dashboards



### Step 3. Communicating trafficlight

Now its time to communicate using a mqtt-library to adafruit.io through the WiFi network. 

On https://io.adafruit.com/
* Create a feed "myfeed" at https://io.adafruit.com/ADAFRUIT_USER_NAME/feeds (replace ADAFRUIT_USER_NAME with your username )
* Create a dashboard:  https://io.adafruit.com/ADAFRUIT_USER_NAME/dashboards/pycom
 * Add a simple Toggle item to the dashboard that you connect to your feed.
* Import the mqtt library. Download [mqtt.py](../lib/mqtt.py) and upload it to the LoPy4 device. 

Then run following code after changing the needed string constants

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
    time.sleep(3)
    print("Sending OFF")
    client.publish(topic="ADAFRUIT_USER_NAME/feeds/myfeed", msg="OFF")
    client.check_msg()
    time.sleep(3)
```


### Step 4. Syncing trafficlights
