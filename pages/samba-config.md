---
layout: page-fullwidth
title: "Samba Share Configuration"
subheadline: "Configuration for Samba Share Setup on Pi3"
permalink: "/samba-share-config/"
header:
   image_fullwidth: "about-us-01.jpg"
   logo: "no"
---

Samba share gives me shared folders on the Pi3 under the share name `"name"` below and makes the folders under `"map"` available for direct editing.

~~~
{
  "workgroup": "WORKGROUP",
  "name": "hassio",
  "guest": false,  <-- Important if you define a username or password
  "map": {
    "config": true,
    "addons": true,
    "ssl": false,
    "share": true,
    "backup": true
  },
  "username": "****",
  "password": "****",
  "interface": "eth0"
}
~~~

**Note: It's important to remember to change `"guest"` from true to false if you define a value in `username` or `password`.