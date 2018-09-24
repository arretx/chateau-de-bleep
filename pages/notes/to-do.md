---
layout: page-fullwidth
header:
  image_fullwidth: header_unsplash_12.jpg
  caption: At the top of Humphrey's Peak
  logo: "no"
subheadline: "To-Do List"
title: "Ideas and Future Plans"
categories:
  - planning
tags:
  - todo list
permalink: "/to-do/"
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

### Shed

#### Sensors

- NodeMCU to handle temperature, humidity, and motion sensing.

#### Switches

- Sonoff switch to control power to the mist system.
- Sonoff switch to turn the compressor on or off.

#### Camera(s)

- Need some sort of camera installation that can deliver images and live video through HA.

### Back Patio

#### Sensors

- NodeMCU to handle temperature, light, humidity, and motion sensing for the back patio.

### Parking

#### Sensors

- Ultrasonic sensors to detect vehicles in parking spots based upon their height.

### Bathrooms

#### Sensors

- NodeMCU to handle temperature, humidity, and motion sensing.

#### Switches

- Z-Wave switch to control lighting.
- Sonoff switch to control exhaust fan.

### Around the House

#### Switches

- Sonoff switches for candle warmers.
- Sonoff switches for desk-lamps / bedside reading lamp.
- Sonoff switch for above kitchen cabinet lighting.

## Automations

- Motion lights and fans for guest bathrooms.  Ideally, to be able to detect when someone is either taking a crap, or showering.  Humidity sensing would turn on the fan in the event of a shower, but I haven't worked out the poop detector.

- Shed lights would be turned on for a period of time when either light is sensed or motion is sensed.  Alarm could indicate an elevated temperature / humidity level.

- Candle warmers on at certain intervals during the day for a set period of time but only when someone is home.

- Vacation Mode.  A way to override all automations that are "vacation sensitive."


</div><!-- /.medium-8.columns -->
</div><!-- /.row -->
