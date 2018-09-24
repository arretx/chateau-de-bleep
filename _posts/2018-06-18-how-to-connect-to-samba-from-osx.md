---
layout: page-fullwidth
header:
    image_fullwidth: "header_unsplash_1.jpg"
    caption: Man typing feverishly on his MacBook Air
    caption_url: https://homeassistant.jongriffith.com
# Content
comments: true
subheadline: "Less is more"
title: "How to connect to Home Assistant through Samba in HASS.io on a Raspberry Pi3"
teaser: "There's no mystery to this.  As long as you've set it up correctly, you shouldn't have any trouble connecting."
tags:
  - samba, sharing, configuration
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

### My Environment

- MacBook Air running OSX High Sierra 10.13.3
- WIFI Network provided by Airport Extreme.
- Raspberry Pi3 hard-wired into router running [HASS.io](http://home-assistant.io/hassio/).
- 32GB SD Card in Pi3

### How to Connect

Assuming you've configured the Samba Add-On in Hass.io and it's up and running:

1. Go to Finder.
2. Click the `Go` menu and select `Connect to Server`
3. Enter `smb://[your_username]@[your_pi3_ip_address]`
4. Connect
5. Enter the password you set in your Samba configuration page. ([2])

Choose which folder(s) you want to create a volume for and voila!  You're connected.  Now you can use whatever program you want to edit the files inside of those folders.

</div><!-- /.medium-8.columns -->
</div><!-- /.row -->

[2]: {{ site.url }}/samba-share-config