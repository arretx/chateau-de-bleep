---
layout: page-fullwidth
title: "Change Log"
meta_title: "Chateau de Bleep Configuration Changelog"
subheadline: 
teaser: "History and changelog of Chateau de Bleep Home Automation"
header:
   image_fullwidth: "header_unsplash_8.jpg"
permalink: "/changelog/"
---

### 6-18-2018 // Complete Do-Over

There seem to be too many errors occurring in the system, and as it was my first attempt a building a home automation hub with Home Assistant (HASS.io specifically) I'm sure there were some screwups along the way that were causing problems.

:	7:30PM // Backed up all of the configuration settings and files from the current setup.
:	7:40PM // Downloaded and unpacked the HASS.IO image.
:	7:41PM // Using Etcher, etched the image to the same flash card used on the previous install.  The old system is _gone_
:	8:45PM // Configured the ResinOS ([1]) file with the correct settings.
:	8:57PM // Ran LanScan IP Scan on the network and found that the device was in fact up and running at 192.168.1.2 with hostname `hassio`.
:	8:58PM // Tested http://hassio.local:8123 and succeeded.  This is going well.
:	9:00PM // Started Samba Share 3.0 installation to be able to edit files on the Pi3's memory card.
:	9:01PM // Turned on Auto Update for Samba Share
:	9:05PM // Set the configuration options for Samba ([2])
:	9:10PM // Started Samba Share.
:	9:16PM // Connected to samba share from Mac OSX. ([3])
:	9:32PM // Completed Article on how to connect to Samba. ([3])
:	9:46PM // Configured Recorder to user MySQL on Ubuntu 16.04 server instead of locally on SD Card.
:	9:52PM // Disabled `cloud:` component due to cognito errors and inability to login to HA cloud from the cloud login page.

**Note**: After looking at the `States` I've noticed that there have been a few entities automatically detected:

- group.all_switches
- media_players (google minis and google home)
- switches (WEMO devices)

**Note**: Initial error log shows Cognito keyset error for `cloud` and a single `updater` error reporting inability to connect to Home Assistant Update to check for updates.

:	9:57PM // Set a system password for Home Assistant interface.
:	9:59PM // Restarted System
:	10:13PM // Installed Let's Encrypt Add-On.
:	10:15PM // Uninstalled Let's Encrypt Add-On.

### 6-20-2018  

:	1:31PM // Enabled `cloud:` component to test connection again.
:	6:10PM // Commented out the `introduction:` component to remove the Welcome Home notification on the gui.
:	6:24PM // Disabled `cloud:` due to continued Cognito errors.
:	6:29PM // Movedt `groups:`, `scripts:`, and `automations:` into their own include folders.

### 6-23-2018

:	Updated system from 0.71 to 0.72.
:	Enabled ZWave and programmed all Z-Wave devices.
:	4:21 // Installed and configured DuckDNS
:	4:21 // Installed and configured MQTT

<div id="videoModal" class="reveal-modal large" data-reveal="">
  <div class="flex-video widescreen vimeo" style="display: block;">
    <iframe width="1280" height="720" src="https://www.youtube.com/embed/3b5zCFSmVvU" frameborder="0" allowfullscreen></iframe>
  </div>
  <a class="close-reveal-modal">&#215;</a>
</div>


 [1]: {{ site.url }}/resin-network-config
 [2]: {{ site.url }}/samba-share-config
 [3]: {{ site.url }}/posts,%20articles/how-to-connect-to-samba-from-osx/
