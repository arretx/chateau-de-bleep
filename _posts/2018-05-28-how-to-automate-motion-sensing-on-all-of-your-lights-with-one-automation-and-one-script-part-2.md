---
layout: page-fullwidth
header:
    image_fullwidth: "header_unsplash_1.jpg"
    caption: This is a caption for the header image with link
    caption_url: https://unsplash.com/
# Content
comments: true
subheadline: "Less is more"
title: "How to Automate Motion Sensing on all of Your Lights with One Automation and One Script"
teaser: "When all is said and done, you can easily have a single script and automation handle all of your home's motion sensing lights."
tags:
  - scripts, automations, lights, motion sensor
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


# The Problem

I was finding myself writing automation after automation to do the same thing for multiple devices.  Knowing that scripts are designed to run the same routine over and over again, it mades sense to create a script that would accomplish a simple goal.

**Goal:** Upon motion detection in a specific location, turn a specific light on for a period of time and then turn it off.  

I wanted to use a single automation.  When a motion sensor's state changes from `standby` to `motion detected` (the trigger), run a script (the action) and turn a light, or group of lights on that are assigned to just that motion sensor.  No conditions were set on this automation, but they could be.

## Information Needed

For this example, we'll stick to a single motion sensor and a single light, but this is ultimately designed to handle multiple lights and multiple sensors.

We need to know a few things to make this automation work.  You need first to know the entity_id of the motion sensor.  In my case, I built one of those DIY motions sensors that BRUH Automations talks about.  So, my motion sensor was found at `sensor.sn1_pir`.

You also need to know the values of the states of the motion sensor.  If you have the same sensor, your values will be `standby` and `motion detected`.

You'll need the entity_id of the light you wish to affect as well.  In my case, I have a Z-Wave dimmer that I've named `light.kitchen`.

## Input Number (optional)

If you want to be able to easily adjust the delay between the light turning on and the light turning off from your dashboard, you can create an `input_number` and you'll have a slider that you can adjust.  Otherwise, you can skip this and just set a static delay time, or no delay at all.  It all depends on where you want to go with this.

I created one called `light_timer_kitchen_seconds` with an initial value of 10, a minimum value of 1, a maximum value of 59, and it steps in increments of 1.

~~~~
light_timer_kitchen_seconds:
  name: Seconds
  initial: 10
  min: 1
  max: 59
  step: 1
~~~~

## The Automation

~~~~
- alias: Motion Lights (optional)
  trigger:
    platform: state
    entity_id: sensor.sn1_pir
    to: 'motion detected'
  action:
    - service: script.timed_light
      data_template:
        value1: >-
          {% raw %}{% set convert = { "sensor.sn1_pir": "light.guest_bedroom" } %}{% endraw %}
          {% raw %}{{convert[trigger.to_state.entity_id]}}{% endraw %}
        value2: "100"
~~~~

So what's happening here?

The trigger section of the automation waits for the state of the motion sensor to change `to: 'motion detected'`. Once this occurs, the action is called.

In the action, the service we call is a script which we'll get to below.  We're going to create a data template so we can pass dynamic values to the script.  The data template we're creating is a multi-line template, and the value, since we're calling the script directly on the `- service:` line will be stored and passed to the script via the variable `value1` and `value2`.  You can name these whatever you wish.

#### Value1

Value1 is going to be assigned from an array that we're going to create on the fly, because it's assumed that we're going to have multiple sensors and multiple lights.  The goal is to assign an entity or group of entities to a sensor in each pairing inside of the array.  In my example, I only addressed a single sensor and a single light.  But, if you wanted to add more, you would simply continue the array:

~~~~
          {% raw %}{% set convert = { "sensor.sn1_pir":"light.guest_bedroom", "sensor.sn2_pir":"light.hall" ... and so on } %}{% endraw %}
~~~~

After the array is created, we need to cherry pick the right light from the array using a template trigger.  

~~~~
{% raw %}{{convert[trigger.to_state.entity_id]}}{% endraw %}
~~~~

We know that `convert` is an array that contains a list of all of the devices we assigned.  `[trigger.to_state.entity_id]` is the value found at the index position that is defined by the sensor that triggered the automation to begin with.

`trigger.to_state.entity_id` will report the entity that triggered the automation.  Since it can be paired with its corresponding light in the array, the value stored in `value1` becomes the light that's associated with the device that triggered the automation.

Now that we have the data we need, it will be properly passed to the script, which needs to receive the information.

## The Script
~~~~
timed_light:
  sequence:
    - service: light.turn_on
      data_template:
        entity_id: "{% raw %}{{value1}}{% endraw %}"
        brightness_pct: "{% raw %}{{value2}}{% endraw %}"
    - delay: "00:00:{% raw %}{{ '%02d' % (states('input_number.light_timer_guest_bedroom_seconds')|int) }}{% endraw %}"
    - service: light.turn_off
      data_template:
        entity_id: "{% raw %}{{value1}}{% endraw %}"
~~~~

The script runs a sequence of three events.  First, it turns the appropriate light on, then it waits for a number of seconds, then it turns the light off.  (Service / Delay / Service)

### Event 1: Turn On Light

Using the information stored in `value1` from the automation, we call up `light.turn_on` using a `data_template` where the `entity_id` is equal to `value1`.  We also set the brightness to `value2` for which we haven't created any input numbers.  It's just a static number at this point.  But, you could easily create a slider and define a user controlled value here.

### Event 2: Delay

Since this particular script is just designed to give us a little bit of light for a short period of time, there's a delay placed between the two light actions.  The delay format is simply "00:00:00" but the last two zeroes are a template that pulls the value of the `input_number` that I created.  It's an integer, and it's prefixed by `%02d` to ensure that it's always a two-digit number.

### Event 3: Light off

We use `value1` again here to shut off the light after the delay.


## Conclusion

Assuming you've named everything correctly and you actually have these devices to play with, you'll have yourself a functioning automation and script that can be written once and used with multiple lights to accomplish the same task no matter where in your house you have the items located.  The size of the array is up to you, and the degree of complexity to which you can take this is unlimited.

Group your lights, create conditions in the automation, affect the levels utilized at different times of the day, disable the automation based upon sleep schedules, etc.

</div><!-- /.medium-8.columns -->
</div><!-- /.row -->
