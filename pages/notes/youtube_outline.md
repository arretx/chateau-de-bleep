---
layout: page-fullwidth
header:
  image_fullwidth: header_unsplash_12.jpg
  caption: YouTube Outline
  logo: "no"
subheadline: "An extremely comprehensive look at my rig."
title: "Modifying Sunday Keys for Ableton for Backing Tracks and more..."
categories:
  - sunday keys
tags:
  - ableton live, sunday keys, ableton, music, mainstage
permalink: "/sunday-keys-for-ableton/"
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

# Basics

This is a very long article, but it's designed to be as comprehensive as possible, and in a logical order as though you were just beginning to setup your rig.  Take it step by step and if you have any questions, start a discussion at the bottom of the article.

## Gratitude

Firstly, let me thank David Pfaltzgraff (he said "faults-graph" when I asked him) over at [SundaySounds.com](http://www.sundaysounds.com) who painstakingly developed a streamlined live instrument rack set for Ableton Live to make the experience of playing live keys in Ableton much...much better for all of us.  Wrapping my mind around how he stayed focused throughout development of the racks is something I may never do, as Ableton routing and mapping can get very confusing at times.

Secondly, another big thank you to [Kristian Ponsford](https://www.kristianponsford.com/) for putting together the worship template that I used to learn how all of this works.

## What You'll Find Here

From start to finish, this article will take you through every step needed to convert Sunday Keys for Ableton Live into a powerful template for live performance with or without backing tracks / multi-tracks.  I'll work through how my keys are routed, how I create click tracks and band cues, how I arrange songs, how I map midi controllers, and how I manage files and folders...etc.

I'll be starting with a brand new copy of Sunday Keys for Ableton Live and I'll walk through the entire process from start to finish, detailing every technique that I've employed, to the best of my ability.

An accompanying video, or series of videos will also follow as soon as I can get them rolling.

## My Hardware

Each of you have your own tools to use as inputs to run Ableton Live.  The following tools are what I'm using, and I'll be going through how to set each one of them up so you have a fairly comprehensive rig.  In addition to the input tools, I've also listed my computer choice, audio interface, lighting controller, and various accessories.

1. Akai Professional Advance61 Keyboard
1. Yamaha CP33 Digital Piano
1. Korg nanoKONTROL2
1. Korg nanoPAD2
1. iPad Pro 10
1. Focusrite Scarlett 18i8 (1st gen)
1. MacBook Air 2014 with 8GB Ram
1. Powered USB Hub
1. DMXIS USB to DMX single universe lighting controller
1. Roland Sustain Pedal (standard style for a digital piano)
1. Novation Launchpad Mini
1. In-Ear Monitors (for monitoring instruments, click track, and band cues, and cueing up original studio recordings for reference.)

## My Software

These tools are essential ingredients and must-haves to keep you on track.

1. OSX on your favorite Mac.
1. Audio Interface drivers / mixer utility.
1. Ableton Live 10 Suite
1. Isotonik Studios FOLLOW Max4Live Device (absolute must have for session backing track arrangements)
1. SoundFlower for loop-back recording on your computer.
1. MIDI Monitor to diagnose MIDI signals.
1. OnSong for iPad - Lead Sheet library
1. DMXIS Plugin / Standalone software to control lights.
1. Sunday Keys for Ableton Live

## Hardware Configuration

Ableton Live basically does two things.  It plays/records and routes audio, and MIDI.  It is assumed that you have a basic understanding of both.

### Audio Setup

You need to make sure you understand your audio interface.  Since I don't know what you have, I cannot go into depth about it, but the principles for every device are basically the same.

Ableton Live needs to know what audio device you're using for input and output.  Once you have set that up, you can start routing audio in and out of Ableton Live.  Please refer to your audio interface manual for details on how to set it up and control it.

### MIDI Setup

All of your MIDI input devices (Keyboards, Faders, Buttons, Push Controllers, Launchpads, etc.) must be configured before you can tell Ableton Live about them.  Each device needs to be set to its own MIDI channel.  Most devices are set, by default, to transmit on a global channel.  Coincidentally, Ableton Live defaults to a global input when creating new tracks.  If two devices are sharing the same resources you _will_ run into conflicts.  You will find that pressing a pad on your NanoPAD2 triggers a note just like if you were playing your keyboard.

So, isolating your hardware MIDI signals needs to be well planned out.

If you don't already have it installed, find any good MIDI Monitoring software, install it, and open it up so you can see what happens when you press buttons on your device(s).

#### Akai Advance61 Keyboard (Keyboard #1)

Set your primary keyboard to transmit on MIDI Channel 1, and only that channel.

**Note: many MIDI devices allow customization of control surfaces to send and receive on multiple channels.  Don't go crazy trying to mix and match things until you have firm grasp of how to troubleshoot conflicts.  Stick to isolating each controller.**

If you have a keyboard at home that is not the same as the keyboard where you perform, make sure they are both set to the same channel so you can plug and go when you move between them.

#### Yamaha CP33 (Keyboard #2)

Since I'm never on stage with more than one keyboard, presently, the Yamaha is my primary performance tool, while the KORG is my rehearsal tool at home.  As such, I can have both keyboards set to transmit on channel 1.  I _am_ limited to mapping controls on one or the other outside of the realm of the notes themselves because the Yamaha has no dials or knobs, and the KORG does.  So I avoid setting up my template to utilize anything other than the basic performance controls for triggering notes in Sunday Keys.

#### Korg nanoKONTROL2

(**Note: If you want to set your nanoKONTROL2 to be in LIVE mode, you will lose some functionality.  When in LIVE mode, Ableton automatically maps buttons and controls, sometimes unfavorably, to the first 8 tracks in the set.  Using non-LIVE mode, rather setting it for CC mode is going to be a better option for complete customization.**)

**How to configure:**

**Hardware Settings:**

1. Disconnect your NK2.
1. Press the SET button and the STOP button (on the transport) on the KN2 simultaneously while plugging in the USB cable.
1. Your device is now in LIVE mode.
1. Download and Install the KORG Kontrol Editor from Korg's website.
1. Open the Editor, choose the NK2 from the devices list and Click "Communication -> Receive Scene Data" or press Command-L.  From what I recall, this may already be a default action every time you select a device.
1. Save your scene set file "File -> Save As" to preserve the current settings.
1. In the "Control" tab, select the Global Midi channel you wish to reserve for this device.
1. Click "Communication -> Write Scene Data" or press COMMAND-T.

Now your device is transmitting on that channel.

**Software Settings:**

1. Open Ableton Live.
1. Go to Live -> Preferences.
1. Click the Link/MIDI tab.
1. Under Control Surface, choose MackieControl (I don't recall if this needed to be installed, or if it's available by default.)
1. Under the Input dropdown, choose nanoKONTROL2 (SLIDER/KNOB)
1. In the MIDI Ports section, turn `Track` and `Remote` on for MackieControl Input (nanoKONTROL2).

(**Note: Enabling `track` sets MIDI devices to be available in the device selector on any given MIDI track.  Enabling `Remote` tells Ableton Live to listen and receive MIDI data for the device.  Since we aren't sending data _back_ to the NK2, we don't need to configure any Output settings.  If we wanted to control the hardware directly through Ableton Live, or from another MIDI device, we would need to setup the Output.  An example would be visual feedback for lighted pads when activated in Ableton.**)

Confirm that your NK2 is working with Ableton by pressing the Play button on the controller while Ableton Live is open.  The clock should begin counting.  Press Stop and it should stop.  Press stop again and the arrangement position should return to 1.1.1.

#### Korg nanoPAD2

My NP2 is set to transmit on MIDI channel 2.  As far as I know, there is no startup configuration to set it to "Live" mode.

**How to configure:**

**Hardware Settings:**

1. In the Korg Kontrol Editor, select the nanoPAD2 device from the File -> Select Device menu, or press COMMAND-D.
1. Click the GLOBAL button in the upper right-hand corner.
1. Save the default settings just in case.
1. Under the `Common` tab, select Global Channel 2, or whatever channel you plan to put your device on.
1. Click the `Write` button.
1. Your MIDI monitor should be reporting activity on the correct channel now.

**Software Settings:**

1. In Ableton Live, go to Live -> Preferences
1. Click the Link/MIDI tab.
1. Under `Control Surface` select MackieControl.
1. For Input, choose `nanoPAD2 (PAD)`.  No output is necessary unless you want your device to receive information.
1. Under MIDI ports, turn `Track` and `Remote` ON for `MackieControl Input (nanoPAD2 (PAD))`.
1. Close preferences.

#### Other MIDI Devices

If you have any other MIDI devices, now would be the time for you to configure them, assign them to a channel, and tell Ableton Live what they are and whether or not it should not only listen for them (Input Track/Remote ON), but also talk back to them (Output Track/Remote ON).

### Audio Setup

Your audio setup will be unique unless you have the same hardware as I do.  The setup is fairly simple.

1. Connect your Audio Interface to your computer.  Ensure the drivers that need to be installed are, and install any of the utilities that are recommended for it.
1. Once you can confirm that your system audio works through the interface, use Ableton's Live -> Preferences to select the Audio tab.
1. Select your interface for input and output.  
1. For each of the input and output settings, you can choose which inputs that Ableton will make available to you in the Track Input/Output settings.  If you choose 1&2, then when you create an audio track, 1&2 will be available in the tracks for audio routing.  This is true for both input and output settings.  If you choose 1 under MONO but not 1&2 under stereo, then you'll be limited only selecting 1 in any given audio track.  Your project(s) will often dictate what you need.  At the bare minimum, you'll probably need to select your audio interface's MAIN Outs (mine are actually 1 & 2) as the Output option.

This will make 1&2 available in the Master Track, and when configured correctly, any track or group of tracks in Ableton that point to the Master track will be sent out on the Output channels selected on the Master fader.

#### SoundFlower

Soundflower is a loop-back plug-in that allows you to record system audio sounds directly into Ableton Live.  For example, if you want to capture sound from YouTube or Spotify on the same machine running Ableton Live without using your audio interface to physically loop a cable back into itself, then you want Soundflower (a free, and as I understand, no longer developed tool) that gives your computer a `virtual sound output`.

This is a must have if you want to capture your favorite artists songs to be used to model an arrangement.


## Modifying the Sunday Keys Template for Backing Tracks

This is where the meat of the matter begins to pile up.  I would assume that you purchased the Sunday Keys for Ableton Live template by this point.  If so, let's dive in.  Modifications you make to this set file are going to be largely custom to your tastes.  I'm going to walk you through how I do it, and you can model that for your setup.

First things first, organize your files.  Bad ableton resource management will come back to haunt you.

## Put the Files in the Right Place

You _could_ unzip your Sunday Keys for Ableton Live zip file and then point Ableton to that folder...OR you could take more control over organizing your Ableton Live libraries and put this in a better location.  Here's how.

1. Unzip the Sunday Keys for Ableton download that you purchased from SundaySounds.com.
1. Open the file `Sunday Keys for Ableton.als` by double clicking it.  Ableton should open.
1. In Ableton, `Click File -> Save Live Set As` and point your browser to your Music folder (/users/<username>/music/).  Youl should already have an Ableton folder in the music folder.
1. In the Ableton folder, create a new folder called `Projects`.
1. Save your live set as `Sunday Keys Original Template` _in the Projects folder_.  This will create a new project with the project configuration files ready to go.
1. Do this again in the same folder, but this time, name the file something like `Sunday Keys Modified` or something that indicates that it's your version of the original set.  Now you've just preserved a copy of the original downloaded set file _and_ you have your own to work with.
1. Go back to the folder where you originally unzipped the Sunday Keys for Ableton Live files and delete the `Ableton Project Info` folder and the `Sunday Keys for Ableton.als` file.
1. Open the Presets folder and rename each folder by adding SK to the front.  For example, change Auxiliary to SK Auxiliary, and Entire Racks to SK Entire Racks, until all of them are changed.
1. Select all of the SK folders you just renamed and copy them to the clipboard.
1. Navigate to your music folder (/users/<username>/music/Ableton).
1. Double click the User Library set.
1. Double click the Presets folder.
1. Paste all 5 of those renamed folders into this Presets folder.

What you've done here is created a project folder in the Ableton folder under your music folder that will handle any and all sets that you create under _this project only_ while at the same time _adding all of the Sunday Keys for Ableton Live resources to your User Library_ which makes them available from your user library to any project you choose to create.

Now you're organized.

## Adding Custom Tracks

(**Note: as mentioned in the software list at the beginning of this article, one of the must have pieces is Isotonik Studio's FOLLOW Max4Live device.  Without that, you will not be able to easily arrange songs for performance in session view.  It can still be done, but it's much more difficult.**)

Open the Sunday Keys set that you created inside of the SK project folder.  Not the original backup, but the one you created to fool around with.

1. Select all of the SK tracks (you won't be able to select the SHIMMER track because it is a return track.)
1. Group them together and name the group `SundayKeys` or something like that.
1. Collapse the group so it's out of the way.  Don't worry, everything is still there.

### MIDI Input Tracks and Groups

1. Create, at the very minimum two new MIDI tracks.  SHIFT-CMD-T twice.
1. Select both tracks and set a common color.
1. Rename (CMD-R) the first track `Keyboards` and the 2nd one after the name of your keyboard.  Mine will be `KORG Advance61`.  In addition to these two tracks, create a MIDI track for every independent hardware device that you configured with its own input channel.  That would be your nanoKontrol2, nanoPAD2, and any other hardware input MIDI devices.
1. Group the tracks you just created (CMD-G).
1. A new group track will be created.  Rename the group track to `MIDI Devices`.
1. Each MIDI track, aside from the Keyboards track in the group you just created needs to be configured for the device that it represents.
1. Select the track for your piano, whatever it may be called.
1. In the `MIDI From` drop-down, select the instrument that you want Ableton to listen to on that track. (if you don't see the drop-down, make sure you can see the I/O section of the track "CMD-OPTION-I"), or View Menu -> In/Out.
1. In the channels dropdown, select the channel that you configured that device to transmit on.
1. Set `Monitor` to IN.
1. Set `MIDI Output` to the name of the `Keyboard` track, which was the first of the two tracks we created in step 2 of this section.  This sends the MIDI directly to the Keyboards track.  The purpose of this is to enable you to use an alternate keyboard that transmits on the same channel as the keyboard you're using _now_ without having to change the settings every time you move between them.
1. On the `Keyboard` track, set monitor to IN.
1. Make sure that `MIDI From` and `MIDI To` are both set to `No Output` on the Keyboards track.
1. On all other MIDI instrument tracks that you've created for your devices, run through the same steps as above, setting the instrument source, channel, monitor to IN, but on all other devices, leave `MIDI To` set to `No Output` unless the signals from that device have an explicit destination that you need to route it to.
1. Collapse the `MIDI Devices` group.

Now we have to properly set the MIDI input for the 8 Sunday Keys MIDI tracks.  By default, they come set to `All INS` on all midi channels.

1. Expand the `SundayKeys` group.
1. Select all 8 of the colored instrument tracks by clicking on `Pianos 1`, holding shift, then clicking on `Auxiliary 2`.
1. Change the `MIDI From` on one of the selected tracks to `Keyboards` and leave `Post Mixer` as it is.  If you utilize any MIDI effects in the future, you can play around with this setting, but for now, leave it as the default.
1. Collapse the `SundayKeys` group and the `MIDI Devices` group.

(**Note: When a track is set to Monitor in, everything that comes into the track will be passed through to the audio destination as set in the `SundayKeys` group track.  This is probably set to Master.  If the track is armed for recording, it will also pass through the track.  There are two things that the ARM button will do.  1.  It enables recording.  If you start recording, anything that runs through these tracks will be recorded.  2. It enables MIDI CC and Note Values that you may or may not have stored in the clips themselves.  If the track is not armed and you have a clip that you want to pre-program with a live MIDI part, you will not hear it as it won't play.  The colors will also gray out if the tracks are not armed.  Suffice it to say, it's not a bad thing to have the tracks disarmed as long as you have Monitor IN set for each track.**)

Now that you've "tuned in" to the Keyboard track, any MIDI that comes through that track will trigger the devices inside of the 8 SK tracks.

### Audio Recording Tracks / Groups

There are going to be times when you want to bring a song you've heard online or on the radio into Ableton Live.  Why?  So you can warp the tempo and pitch to the key you're choosing to play it in, and use it as your arrangement reference and as a reference for your band during rehearsal.  Naturally you're not goint to be playing the recording live, but you are using it as your baseline to arrange your version of the song.

There may also be times when you want to record your _own_ performances and present them as backing tracks.  Dedicating a track, or group of tracks to handle recording input is how you would do that.

1. Create a new audio track.  Give it an appropriate name.  If you anticipate that you'll have multiple instruments being recorded simultaneously, or an instrument and vocals, you could create additional tracks and and set their inputs according to the hardware you're using or the instrument you're using.
1. Group your track, or tracks, even if there's only one.
1. Name the group `Original Recordings`.

(**Note: If you want to record something into Ableton Live from YouTube, Spotify, Soundforge or some other internal audio source that's playing on the same computer that's recording, you'll need a loopback utility like Soundflower, which will allow you to create a virtual audio interface that sends the audio into the magicsphere.  Then you set Ableton Live's input to listen to the same channel that your system output has been set to, which will most likely be Soundflower (2CH), and you record.)

#### SoundFlower (2CH)

You'll need to download SoundFlower or some other loopback software utility to create a virtual audio interface on your system.  You will then tell your system to use that audio interface as the output device.  In Ableton, you'll set the input to that same device, and from there, you'll be able to play the original recording and record it into a track in Ableton Live.  There _will_ be latency on the recording, so if you're pulling something from a video, the video and the music will be out of sync while recording.  Simply switch back to your regular audio interface after you're done recording before you begin to work on anything else.

## MIDI Cue Tracks

Whether it's click tracks, band cues, lighting cues, ProPresenter cues, or ... well, any cues that _do_ domething other than play notes and automate track elements, this is the section that will explain how to make it happen.

You're going to be sending MIDI one of 3 ways, for the most part.

1. To and from an attached, physical piece of hardware, with a cable.
1. To and from a device via the local WIFI network or Bluetooth.  (Bluetooth is spotty with some applications)
1. To and from a virtual MIDI bus called the IAC Bus.

#### Physical Connection

Simple as can be.  Just connect your device, set it up according to its instructions and Live's MIDI setup in preferences, and you've got yourself a MIDI device that can receive signals.

#### WIFI Network

_When to use:_  When you want to send MIDI to another computer, tablet, phone, etc., on your WIFI network.

This is where things get powerful.  And, you may also level up when it comes to understanding WIFI networks.  You'll benefit by ensuring that your rig and all of its WIFI devices are on an isolated WIFI network that isn't shared with the rest of the congregation.  The less happening, the better.  In a small environment, you should be okay, but when the network starts to get big, it might be best to simply have a dedicated WIFI router on stage to connect all of your production machines.  You may need a network administrator to help you get this setup properly.

1.  In OSX, open the Audio/Midi Setup from Spotlight (or even better, from Alfred, which is way better than spotlight.)
1.  Press `Command-1` to open the MIDI Studio
1.  Double click the Network icon.
1.  Enable Session 1 under `My Sessions`.  If there is no Session 1, create one.
1.  Make sure it's enabled.
1.  Any device on the network that is receptive to MIDI through WIFI will show up in the Directory below My Sessions.  Find the device you want to connect to, click it, and connect to it by clicking `Connect.`  If all goes well, you'll see the same device show up in the `Participants` window.  Now you're connected to that device.
1.  Some mobile devices that can be controlled via MIDI won't show up in the available devices until the app that you need to control is running on that device.  A good example of this would be OnSong.

I have found that if there are multiple devices that you need to connect to, do it within the same Session rather than creating a new Session for each device.  You're bound to lose your mind if you try to do it that way.

#### IAC Bus (Inter-Application Communication)

_When to use:_ When you want to send MIDI between applications on the same computer.

The IAC Driver creates a virtual MIDI bus that sends MIDI into the magisphere from any given app that you're using to generate MIDI output.  Then, any other app, or even that same app can listen to the IAC Bus for incoming signals and use them.  This is how we send MIDI from one DAW to another.

An example of this would be when we use Ableton Live to control a feature inside of MainStage.

Another example would be when we want one track in Ableton Live to control MIDI assignable elements _outside_ of the track that the MIDI data is being sent from.  One example of this would be controlling the mute button on track 2 from a clip in track 1.  Or, perhaps we want automation in a clip to control the stop button on the transport control, which isn't inside of any track.  The IAC Bus can do that.

### Click Track / Band Cues / Band Cue Repeat

The click track and band cue tracks are setup identically, but their content is different.  Each of these tracks uses a Drum Rack in Ableton Live that plays a sample for each sound you want.  The click track typically has two sounds, but can be anything you want, and the Band Cues track has a single sample of multiple cues, sliced up so only a portion of the sample is triggered, yielding only a single word or phrase from that sample.

Create a click track:

1. Insert a new MIDI track.
1. Rename it `Click Track`.
1. Set the MIDI From to `No Input` and the MIDI To to `No Output.`  The click track is only going to play notes in clips _in the track itself_ that trigger the corresponding note pads on the drum rack, which we're about to add.
1. Set the Audio To so it's routed to an alternate set of outputs on your audio interface.  (**Note, if you're using internal audio on your computer system, which is often limited to a single stereo L/R output, you may find that you'll have to simply split your L/R signal, sending clicks and cues to channel 2 and everything else to channel 1.  With a y-splitter on the output that separates the signal, you can send each to its own amplification system.**)
1. In Ableton Live, under Drums in the file browser, drag a Drum Rack and drop it on the Click Track.

Your next goal is to locate two sounds that could be used for your metronome, both a downbeat, and upbeats.  You could, if you prefer, just drag an entire drum kit as provided in the core Ableton library, to the Click Track.  It's up do you.  The only thing you'll need to know is which note value corresponds to the drum pad for the sound in the kit you chose, because that's what we're going to trigger when we create our metronome MIDI clip.

1. Drag and drop your sounds on the drum pads of your choice.
1. In the `Click Track`, on one of the scenes, double click a clip slot in the Click Track to create a new one bar clip.
1. 

You will want to create a group of tracks to handle cues.

Click track choices are a personal preference.  You'll have to play around with the sounds that make the most sense to you.  Let's get started.

1. Create a new MIDI track.  This track will not need input

### Video: How to record an internal audio source such as YouTube or Spotify in Ableton Live 10

1. Create an Audio track to handle original artist recordings.



1. Create a combination of audio and midi tracks to handle audio for in-ear monitoring.
    1. Create a click track with a drum rack.
    1. Create a band cue track.
    1. Create a band cue repeat track.


</div><!-- /.medium-8.columns -->
</div><!-- /.row -->
