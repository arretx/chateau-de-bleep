---
layout: page-fullwidth
title: "ResinOS System Connections Configuration"
subheadline: "Configuration file for ResinOS on the Pi3"
permalink: "/resin-network-config/"
header:
   image_fullwidth: "about-us-01.jpg"
   logo: "no"
---

This configuration setup worked for me on my instance of HASS.io as of 6-18-18.

After flashing the SD card with the HASS.io image, theres a file on the card that needs to be edited.

**Location**: /system-connections/  
**File-Name**: resin-sample  
**Renamed to**: resin-ethernet (cause it was prettier?)

Simply edit this with a text editor and save it.  I renamed mine to `resin-ethernet` because I was switching from a WIFI configuration to an ethernet only configuration.

~~~
[connection]
id=my-ethernet
type=ethernet
interface-name=eth0
permissions=
secondaries=

[ethernet]
mac-address-blacklist=

[ipv4]
address1=192.168.1.2/24,192.168.1.1
dns=8.8.8.8;8.8.4.4;
dns-search=
method=manual

[ipv6]
addr-gen-mode=stable-privacy
dns-search=
method=auto
~~~

The only part I was unsure of was the `interface-name` line.  I wasn't sure if the Pi3 called the port `eth0` or not, but I went with it, and it worked.

The `address1` line shows first the IP address I had reserved on my router.  I used the MAC address I had previously captured when it was last up and running and assigned it to this address in my router.  The `slash 24` indicates that it is a 24-bit subnet mask address (i.e. 255.255.255.0) which I am limited to by my router.  This could be anything if your topology is different.

The last part of the `address1` line is the router's address.  DNS is set to use Google's servers.