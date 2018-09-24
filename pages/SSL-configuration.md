---
layout: page-fullwidth
title: "Let's Encrypt Add-On"
subheadline: "How to set up HASSIO with Let's Encrypt"
teaser: "This will help you set your system up with a secure connection."
permalink: "/SSL-configuration/"
header:
   image_fullwidth: "header_unsplash_22.jpg"
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

**Note**: According to [the official add-on page](https://www.home-assistant.io/addons/lets_encrypt/) for Let's Encrypt, if you're using the DuckDNS add-on, you will not want to use the Let's Encrypt Add-on, as SSL is already addressed by DuckDNS.

I host my own name server and HASS.io runs behind my network router, so my domain name is already pointed to my public IP address.

## Steps:

1. In HASS.io, head over to the Hass.io link in the left menu.
1. Click the `ADD-ON STORE` tab at the top.
1. In the official add-ons, click the `Let's Encrypt` add-on.
1. Click `Install`.
1. As soon as the installation has completed, update your config settings:



</div>
</div><!-- /.row -->



 [1]: {{ site.url }}/resin-network-config
 [2]: {{ site.url }}/samba-share-config
 [3]: {{ site.url }}/posts,%20articles/how-to-connect-to-samba-from-osx/
