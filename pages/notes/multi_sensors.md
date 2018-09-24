---
layout: page-fullwidth
header:
  image_fullwidth: header_unsplash_12.jpg
  caption: At the top of Humphrey's Peak
  logo: "no"
subheadline: "Multi Sensors"
title: "Multi Sensors"
categories:
  - sensors
tags:
  - sensors, pir, motion, light, lux, led, temperature, humidity
permalink: "/multi-sensors/"
---
<div class="row">
<div class="medium-4 medium-push-8 columns" markdown="1">
<div class="panel radius" markdown="1">
**Table of Contents**
{: #toc }
*  TOC
{:toc}
</div>
</div><!-- /.medium-4.columns -->
<div class="medium-8 medium-pull-4 columns" markdown="1">

# HARDWARE 

## MAIN CONTROL BOARD

### NODEMCU 1.0

The multi-sensors that I use are based upon the ESP8266 chip mounted on the NODEMCU1.0 board, which comes with a mini USB connector for power and flashing.

## SENSOR INPUT HARDWARE

### [KY-018 Light Sensor](https://www.aliexpress.com/item/KY-018-photosensitive-Optical-Sensitive-Resistance-Light-module-detects-resistor-module-for-arduino-diy-kit-sensor/32701608104.html?spm=a2g0s.9042311.0.0.5d874c4dzWBybq)

![](/images/ky-018.jpg)

|PIN|Function|
|---|---|
|S|Signal|
|Middle Pin|+5V Power|
|-|Ground (GND)|

### Quick Setup

Please note that these configuration notes are specific to my installation of HASS.io on my Pi3.  Your file locations and naming conventions may be different.

#### Prepare NODEMCU

1. Prepare BRUH Automation Script from REPO for new NODEMCU Board.
1. Check script in Arduino IDE.
1. Flash Board.
1. Wire up sensors and power up node.

#### Configure Home Assistant

1. Restart HASS.io and check known_devices.yaml for newly detected device.
1. Rename device in known_devices.yaml.
1. Create configuration file under **/config/lights/**
1. Create group for new sensor node **/config/group/**
1. Add group to sensor node view **/config/group/**
1. Create mqtt sensors **/config/sensors/mqtt_sensors/sensor_node_[x]**
    - One each for:
      - sensor_node_[x]_humidity
      - sensor_node_[x]_temperature
      - sensor_node_[x]_pir (Motion)
      - sensor_node_[x]_ldr (Light level)

**The LED Light is recognized without needing to connect the LED light to the board and is part of the _light_ domain**.

## Regarding Power

When it comes to powering the sensor, you are able to use a 5V power adapter with a MINI-USB connector, or you can use a USB charging port to deliver power to multiple devices over a standard USB A to MINI cable.

## Functions

The multi sensors sense the following:

- Motion
- Temperature
- Humidity
- Light Levels

They have also been setup with a multi-color RGB LED light.

# Configuration and Naming Conventions

All of the NODEMCU Multi-sensors follow this naming convention:

### BRUH Automation Script Specific Setting

- MQTT Light State Topic: "chateaudebleep/sensornode[X]" where X is the number of the node in sequence.  
- MQTT Light Set Topic: "chateaudebpleep/sensornode[X]/set"

**Multi-sensors are found in the following files and file locations:**

### configuration.yaml

Under the `light:` configuration (approximately line 103) which is included from /config/lights/

- File Names: `sensor_node_1.yaml`, `sensor_node_2.yaml` and so on.

Each file contains configuration information for a single sensor that looks like this:

~~~~
platform: mqtt_json
name: "SN[X] LED" # Where X is the same number as the node number in sequence.
state_topic: "chateaudebleep/sensornode[x]"
command_topic: "chateaudebpleep/sensornode[x]/set"
brightness: true
flash: true
rgb: true
optimistic: false
qos: 0
~~~~

### known_devices.yaml

This file is created when the `nmap:` component is configured.  NMAP scans the network IPs for devices and creates a list of available devices and mac addresses, etc.  Keep reading to find out about how I use this to manage the presence detection of the sensor should it go offline.

Each sensor, when detected by Home Assistant, will appear in the known_devices.yaml file in the Home Assistant root.

Initially the device will appear as follows with the MAC address as its name:

~~~~
b4e62d34da46:
  hide_if_away: false
  icon:
  mac: B4:E6:2D:34:DA:46
  name: 
  picture:
  track: true
~~~~

Which we change to:

~~~~
multi_sensor_2:               <--- Name
  hide_if_away: false
  icon: mdi:flash-circle      <--- icon of choice
  mac: B4:E6:2D:34:DA:46
  name: NodeMCU Multi-Sensor 2  <--- Friendly Name
  picture:
  track: true
~~~~

### groups.yaml  /config/group/

Each sensor node gets its own group and all devices on the sensor are added to that group.  Each sensor group is added to a sensor node view (tab across the top) on the main HA user interface.

~~~~
sensor_node_[x]:
  name: Sensor Node [x]
  view: no
  entities:
    - sensor.sn[x]_temperature
    - sensor.sn[x]_humidity
    - sensor.sn[x]_pir
    - sensor.sn[x]_ldr
    - light.sn[x]_led
~~~~

And the view:

~~~~
sensor_node_view:
  name: Sensor Nodes
  view: yes
  entities:
    - group.sensor_node_[x] where x is the number of the sensor node.
    - group.sensor_node_[x]
~~~~

### multi_sensor_status.yaml  /automation/utility/

The multi_sensor_status file currently defines automations for sensor.sn1 based upon the device_tracker instance of the multi_sensor.

Since I'm using `nmap:` in my configuration, and the multi-sensors obtain an IP address from the router when they come online, nmap scans them and places them in the known_devices.yaml.  This adds them to the device_tracker domain which has a status of either `not_home` or `home`.

#### Automation Details

With the following automation, I can automatically run the `device_offline` script to announce that a given device has gone offline.

"When the state of the device_tracker.multi_sensor_1 changes from 'home' to 'not_home', run the `device_offline` script."

~~~~
- alias: MultiSensor Offline
  trigger:
    - platform: state
      entity_id: device_tracker.multi_sensor_1
      from: 'home'
      to: 'not_home'
  action:
    service: script.device_offline
~~~~

#### Script Details

**File Location**: /config/scripts/  
**File Name**: device_offline.yaml

~~~~
device_offline:
  alias: MultiSensor Offline
  sequence:
    - service: tts.google_say
      entity_id: media_player.kitchen_speaker
      data:
        message: "Multi Sensor Offline"
~~~~

"When an automation fires this script, we'll tell Google Home to say whatever is defined in the message data."

Duplicate automation and script for device ONLINE are also part of the routine.


</div><!-- /.medium-8.columns -->
</div><!-- /.row -->
