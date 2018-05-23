---
#
# Use the widgets beneath and the content will be
# inserted automagically in the webpage. To make
# this work, you have to use › layout: frontpage
#
layout: frontpage
header:
  image_fullwidth: header_unsplash_12.jpg
  caption: At the top of Humphrey's Peak
  logo: "yes"
widget1:
  title: "About The Project"
  url: 'https://homeassistant.jongriffith.com/about-the-project/'
  text: '<em>Not long ago</em> I installed a WeMo switch for my patio lights.  I thought, how cool would it be to be able to turn my lights on and off from my phone.  <br /><br /><strong>Boy was I wrong...</strong>'
widget2:
  title: "What is Home Assistant?"
  url: 'https://homeassistant.jongriffith.com/chateau-de-vie/'
  text: '<em>Home Assistant</em> is open source software that gives you a central hub to control and automate over 1000 different types of devices from switches, to openers, to outlets, notifications...the list is really endless and your limits are your imagination.'
widget3:
  title: "Download Theme"
  url: 'https://github.com/Phlow/feeling-responsive'
  image: widget-github-303x182.jpg
  text: '<em>Feeling Responsive</em> is free and licensed under a MIT License. Make it your own and start building. Grab the <a href="https://github.com/Phlow/feeling-responsive/tree/bare-bones-version">Bare-Bones-Version</a> for a fresh start or learn how to use it with the <a href="https://github.com/Phlow/feeling-responsive/tree/gh-pages">education-version</a> with sample posts and images. Then tell me via Twitter <a href="http://twitter.com/phlow">@phlow</a>.'

#
# Use the call for action to show a button on the frontpage
#
# To make internal links, just use a permalink like this
# url: /getting-started/
#
# To style the button in different colors, use no value
# to use the main color or success, alert or secondary.
# To change colors see sass/_01_settings_colors.scss
#
#callforaction:
#  url: https://tinyletter.com/feeling-responsive
#  text: Inform me about new updates and features ›
#  style: alert
permalink: /index.html
#
# This is a nasty hack to make the navigation highlight
# this page as active in the topbar navigation
#
homepage: true
---
welcome
