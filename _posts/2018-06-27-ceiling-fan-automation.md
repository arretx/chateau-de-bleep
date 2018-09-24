---
title: Ceiling Fan Automation
layout: page-fullwidth
header:
  image_fullwidth: header_unsplash_1.jpg
  caption: This is a caption.
  caption_url: https://homeassistant.jongriffith.com
show_meta: true
comments: true
author: jon
subheadline: Using Temperature Sensors to Trigger Your Ceiling Fans
teaser: How about having all of your ceiling fans become smart?  That's what I've
  done with the help of the NODEMCU1.0 with the ESP8266 chip and a few cheap sensors
  from Aliexpress.
categories:
- automations
tags:
- ceiling fans, zwave, scripts, variables, environment
---

The challenge was simple.  Using a NODEMCU1.0 Sensor Module to read the value of a temperature sensor, relay that information to Home Assistant wirelessly and automatically turn all of our home's ceiling fans on.

Initially creating this automation was a breeze, so to speak, but I quickly realized that I would need a more versatile and lighter weight solution.  By lighter weight I mean _less code_.  I had an automation for every sensor and every fan, which is inefficient.

So, after configuring all of my sensors to work with Home Assistant, I set out to to accomplish the following:

1. Provide a way to set a temperature threshold through either the Home Assistant iOS app, or a control panel on a touch-screen.  This would be the temperature at which the fans would turn on.  This number could be hard coded, but I was determined to create some sort of user input to adjust the threshold until I knew what the right number was.
2. Create an automation that would identify which sensor was the trigger, and only turn on the fan associated with _that_ sensor.  There's no sense in turning on every fan at the same time.
3. Store that information in variables in the automation.
4. Pass that information to a script that would execute a particular routine over and over again, turning a single fan on high for one minute, then reducing the speed to low.
5. Shut each fan off when the temperature fell below the user set threshold.
6. Keep a log of every time each fan was started and stopped.

**Note: user input to select the startup and followup speeds would enhance control, but for now, I hard coded `high` and `low` as the startup and followup speeds.**

I have accomplished the goal...

### Hardware Required
Aside from having an instance of Home Assistant operating on your home network on a computer, or a Pi3, you'll need a GE Z-Wave Plus 3-Speed Fan Switch to replace your fan switch in the wall, and you'll need a Z-Wave Controller configured on the hardware you've used to run Home Assistant.  The Z-Stick is what I have attached to my Raspberry Pi, and it does the trick.

### So what happens now?
From the Home Assistant dashboard, or iOS app, I can use a slider to set the temperature threshold.  If, for example, the temperature of the room where the kitchen fan is located falls below that threshold, Home Assistant will trigger a script that will turn the kitchen fan on high for one minute, then lower the speed to low until the temperature of the room falls below the threshold, at which point the fan will automatically shut off.

### The Automation (Turning On)

#### Trigger

~~~
- alias: Ceiling Fans On at Temp
  trigger:
    platform: template
    value_template: >-{% raw %}
      {% if states('sensor.sn1_temperature') >= states('input_number.fan_temp_threshold') %}
          true
      {% elif states('sensor.sn2_temperature') >= states('input_number.fan_temp_threshold') %}
          true
      {% elif states('sensor.sn3_temperature') >= states('input_number.fan_temp_threshold') %}
          true
      {% elif states('sensor.sn4_temperature') >= states('input_number.fan_temp_threshold') %}
          true
      {% endif %}{% endraw %}
~~~
Triggers are evaluated by default as "or" so often you'll add more than one platform inside of a trigger.  But, when you use a Template Trigger, since you're always evaluating a trigger based upon a `true` or `false` result, you can test multiple entities with `if` and `elif`.

#### Condition

~~~
  condition:
    condition: template
    value_template: "{% raw %}{{ states('binary_sensor.nobody_home') == 'off' }}{% endraw %}"
~~~
There's only one condition for the fans, currently, and that's to check to see if HA thinks nobody is home.  If nobody is home, the binary sensor will be on, so if it's off, then someone is home, and that means that we can proceed with the automation.

~~~
  action:
    - service: script.ceiling_fan_threshold_on
      data_template:
        value1: >-{% raw %}
          {% set convert = { "sensor.sn1_temperature":"fan.kitchen",
            "sensor.sn3_temperature":"fan.living_room",
            "sensor.sn2_temperature":"fan.master_bedroom",
            "sensor.sn4_temperature":"fan.guest_bedroom"} %}{% endraw %}
          {{convert[trigger.entity_id]}}
        value2: "high"
        value3: "low"
~~~
The action calls a script and passes values stored in variables to the script.  The 3 variables used are `value1`, `value2`, and `value3`.

**Value1:** Represents the entity_id of the device that tested true when the trigger template fired.  The entity_id is stored in a dictionary assigned the value `convert` and is then referenced by index position in the template.  This ensures that the correct fan will be activated when the trigger is tripped.

**Value2:** a static hard coded value for the Z-Wave Fan Dimmer.  Ultimately this will be based upon user input to suit the comforts of the individual who spends most of their time in that room.

**Value3:** just like `value2`.

Values 2 and 3 are there because the script is designed to fire up the ceiling fan at one speed for a full minute, then switch to a slower speed after that.

### The Script (Turning On)
~~~
ceiling_fan_threshold_on:
  sequence:
    - condition: template
      value_template: "{% raw %}{{ is_state(value1, 'off') }}{% endraw %}"
~~~
The script's condition simply tests to see if the fan is already on.  If it is, then it's possible that someone manually enabled the fan and it should not be disturbed.

~~~
    - service: fan.set_speed
      data_template:
        entity_id: "{% raw %}{{value1}}{% endraw %}"
        speed: "{% raw %}{{value2}}{% endraw %}"
~~~
We call the `fan` component and `set_speed` without using the `fan.turn_on` component because setting the speed simply turns the fan on.  The entity affected and the speed setting is set by the variable from the automation.

There is then a 1 minute delay.
~~~
    - delay: '00:01:00'
~~~

And after that, we set the speed to the 3rd value from the automation, on the same triggered entity.
~~~
    - service: fan.set_speed
      data_template:
        entity_id: "{% raw %}{{value1}}{% endraw %}"
        speed: "{% raw %}{{value3}}{% endraw %}"
~~~