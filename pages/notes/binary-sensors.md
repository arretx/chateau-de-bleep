---
layout: page-fullwidth
#
# Content
#
subheadline: "Configuration Notes"
title: "Binary Sensors"
categories:
  - sensors
tags:
  - binary sensors
permalink: "/binary-sensors/"
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
Binary sensors are found in /config/binary_sensors in the follwing files:

## binary_sensors.yaml

### Platforms

#### mqtt

Purpose: utilize MQTT message payloads to set the state of a sensor to either on or off depending upon the payload_on or payload_off message.

- **state_topic**: dummy/floorplan/sensor
- **name**: Floorplan

#### template

Purpose: create sensors that are based upon templates that pull information from devices.

- **sun_down**: Checks the elevation of the sun (sun: in configuration.yaml).  If the elevation falls below .10 degrees, the sensor is on.
- **botvac_docked**: Checks the status attribute of the Botvac D5 vacuum.  If the current status is either `Docked` or `Charging` the sensor will be on.
- **dark_in_here**: Light levels inside the home during the day are lower than outside.  This sensor is designed to measure the interior light levels ahead of the actual angle of the sun as inside lighting and outside lighting is handled differently.
- **sunday_serving_alarm**:

- **all_are_home**: If the state of Jon's phone  
`{% raw %}{{ states('device_tracker.jons_iphone_7') == 'home' }}{% endraw %}`  
is 'home' _and_ the state of Melanie's phone  
`{% raw %}{{ states('device_tracker.melanies_iphone_7') == 'home' }}{% endraw %}`  
is 'home' then this sensor is on.
- **nobody_home**: The opposite of **all_are_home**.  Instead of `==`, we write `!=` (not equal to.)
- **only_jon_home**:  Tests to see if Jon's phone _is_ home and Melanie's phone _is not_ home.  This could be written as a test to see if one phone's status is 'not_home' but that would not test true the moment the phone entered another valid zone defined in the zone component, such as the gym, or church, etc.
- **only_melanie_home**: Same as **only_jon_home** but reversed conditions.

## device_status.yaml

</div><!-- /.medium-8.columns -->
</div><!-- /.row -->
