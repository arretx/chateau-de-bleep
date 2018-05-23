---
layout: page-fullwidth
title: "Sensors"
subheadline: "List of Home-Assistant Sensors"
permalink: "/sensors/"
header:
   image_fullwidth: "header_roadmap_2.jpg"
---
<div class="row">
<div class="medium-4 medium-push-8 columns" markdown="1">
<div class="panel radius" markdown="1">

</div>
</div><!-- /.medium-4.columns -->



<div class="medium-8 medium-pull-4 columns" markdown="1">

## Binary Sensors   {#edit-navigation}

### Platform - Template

The following template sensors were manually created to accomplish some sort of automation goal or visual indicator.

#### binary_sensors.yaml

- **binary_sensor.sun_down**: "on" when the sun falls below elevation 0.10.  
- **binary_sensor.botvac_docked:** "on" when the current status of the device is either `Docked` or `Charging`  
- **binary_sensor.dark_in_here:** "on" when the sun's elevation falls below 10 degrees above the horizon.  
- **binary_sensor.all_are_home:** "on" when Jon's and Melanie's phones are both detected by nmap per the device_tracker setup.  
- **binary_sensor.nobody_home:** "on" when both Jon's and Melanie's iPhones are undetected by nmap.  
- **binary_sensor.only_jon_home:** "on" if Melanie's phone is away and Jon's is not.  
- **binary_sensor.only_melanie_home:** "on" if Jon's phone is away and Melanie's is not.  

#### device_status.yaml

The following Sensors were created for the sole purpose of generating a status update board to see which devices were online and ready.




</div><!-- /.medium-8.columns -->
</div><!-- /.row -->

 [1]: http://kramdown.gettalong.org/converter/html.html#toc
 [2]: {{ site.url }}/blog/
 [3]: http://srobbin.com/jquery-plugins/backstretch/
 [4]: #
 [5]: #
 [6]: #
 [7]: #
 [8]: #
 [9]: #
 [10]: #
