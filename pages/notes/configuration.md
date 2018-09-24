---
layout: page-fullwidth
#
# Content
#
subheadline: "Current Configuration"
title: "Configuration Notes"
categories:
  -
tags:
  -
permalink: "/notes/"
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
My instance of Home Assistant is installed on a Pi3 using the HASS.io installation.

# Core Configuration

**Overview:** The core configuration outlines each section of the configuration file and explains what each line is for.
## Configuration Variables

**File Name: configuration.yaml**

### **homeassistant**:

- **name:** the name of our home for this instance of HASS.io.
- **latitude / longitude:** the mapped location of our instance of HASS.io.
- **elevation:** the elevation at home base.
- **unit_system:** imperial (English as opposed to Metric)
- **time_zone:** the time zone of the home base instance of HASS.io
- **customize**: !include customize.yaml.

### **config**:  
Enables the configuration panel in the front end UI (User Interface.)

### **cloud**:  
Adds an additional configuration panel for the Home Assistant Cloud service to the configuration panel in the UI.

### **http**:
Enables the web interface for working with HASS.io.

- **api_passowrd:** The main password for your instance of Home Assistant.
- **cors_allowed_origins:** I honestly have no idea why this is enabled.
- **base_url:** The URL where we are found on the internet.
- **ssl_certificate**: !secret
- **ssl_key:** !secret

### **updater**:
Enables the ability for HA to check for updates.

### **discovery**:
For devices that are supported, this enables auto discovery of those devices.

### **history**:
Enables the ability to track state change history over time.

### **sun**:
Turns on the sun tracking.

### **map**:
Turns on a map in the front end that shows you where tracked devices are.

### **tts**:
Text to speech configuration.

~~~
  - platform: google
    cache: false
    cache_dir: /tmp/tts
    time_memory: 300
  - platform: marytts
    host: 'localhost'
    port: 59125
    codec: 'wav'
    voice: 'cmu-slt-hsmm'
    language: 'en-US'
  - platform: amazon_polly
    aws_access_key_id: !secret
    aws_secret_access_key: !secret
~~~~

## Include Folders

### Automations

**automation**: !include_dir_merge_list automation/  

### Sensors

#### [Binary Sensors](./binary-sensors/)




</div><!-- /.medium-8.columns -->
</div><!-- /.row -->
