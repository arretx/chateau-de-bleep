---
layout: page-fullwidth
header:
  image_fullwidth: header_unsplash_12.jpg
  caption: At the top of Humphrey's Peak
  logo: "no"
subheadline: "Multi Sensor Quick Reference"
title: "Multi Sensor Quick Reference"
categories:
  - sensors
tags:
  - sensors, pir, motion, light, lux, led, temperature, humidity
permalink: "/multi-sensor-quick-reference/"
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

## Overview

Multi-Sensors connect via WIFI using the ESP8266 board (NODEMCU1.0) which comes with a micro USB connector for easy power and programming.  

They detect:

- Temperature
- Humidity
- Light Level
- Motion

and they deliver this information using an MQTT Broker, much like the one that can be installed and used with Home Assistant.

## Arduino IDE

Multi-Sensors are configured using the Arduino IDE Zip downloadable, with the appropriate libraries installed.

- Support for the ESP8266 boards. 

    - You can add it to the board manager by going to File -> Preference and pasting http://arduino.esp8266.com/stable/package_esp8266com_index.json into the Additional Board Managers URL field.
    - Next, download the ESP8266 dependancies by going to Tools -> Board -> Board Manager and searching for ESP8266 and installing it.  

- You will also need to download the follow libraries by going to Sketch -> Include Libraries -> Manage Libraries:

    - DHT sensor library 
    - Adafruit unified sensor
    - PubSubClient
    - ArduinoJSON




</div><!-- /.medium-8.columns -->
</div><!-- /.row -->
