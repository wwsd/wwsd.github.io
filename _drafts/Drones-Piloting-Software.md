---
title: Build your own Drone
description: Why pay lots of money for a toy you KNOW you are going to break?
published: true
layout: post
disqus: yes
fbcomments: no
category: drone
tags:
  - arduino
  - drone
  - openpilot
---

Why pay lots of money for a toy you KNOW you are going to break?  Instead let's build our own so we know we can repair it easily and cheaply, plus we'll get to choose our own components, and later on when we want to scale up we can just remove the brains, build a new frame and attach bigger motors!  Moar power!  Mwahahahahahahah!

### Pilot Software

Let's start with the brains of the matter, there are quite a few choices out there, I'm going to stick to the open source stuff so we can hack on it.

[Ardupilot](http://ardupilot.com/) is a nice place to start, take a robot add an arduino and you got yourself an autonomous pet to do your bidding.  
They also made the [Mission Planner](http://planner.ardupilot.com/) software you'll see everywhere
They seem to be sponsored or related to [diydrones](http://diydrones.com/)

[pixhawk](https://pixhawk.org/choice) seems to be a popular choice albeit with dedicated hardware 
and bit higher of a price this seems to be an up and coming feature rich option

[Paparazzi](http://wiki.paparazziuav.org/wiki/Main_Page)

[DroneCode](https://www.dronecode.org/)

[Open Pilot](https://www.openpilot.org/)

### Radio TX

Every RC enthusiast needs big honking Radio Controller to shout to the world about their nerdliness.
Beware of the ultra cheap stuff, like this Hobby King [4ch TX and RX](http://www.hobbyking.com/hobbyking/store/__8337__Hobby_King_2_4Ghz_4Ch_Tx_Rx_V2_Mode_1_.html)
That will not drive all the channels necessary for our flight apparatus.
But you also don't need an expensive [Futaba 18MZH](http://www.hobbyking.com/hobbyking/store/__8337__Hobby_King_2_4Ghz_4Ch_Tx_Rx_V2_Mode_1_.html)
You can find some really cool retro stuff out there like this
[Taranis X9E](http://www.hobbyking.com/hobbyking/store/__87932__Taranis_X9E_Mode_2_non_EU_Version_US_Plug_.html)
That thing looks great and is expandable to 32 channels, has speech output, telemetry, all the bells and whistles
The [Taranis X9D](http://www.hobbyking.com/hobbyking/store/__67752__FrSky_2_4GHz_ACCST_TARANIS_X9D_PLUS_and_X8R_Combo_Digital_Telemetry_Radio_System_Mode_2_.html)
is a step down but comes with the receiver module

#### 9XR

But I wanted open source so we can hack with the code.  Looking around I found that the turnigy 9x series had an open source firmware out there:
Turnigy 9X open source [firmware](http://www.instructables.com/id/Transform-a-cheap-RC-Transmitter-with-Custom-Firmw/)
Even better this had evolved into the 9XR and now has multiple different open source firmwares for it, here’s the radio:

<http://www.turnigy9xr.com/>

And now there is a [9XR Pro](http://www.hobbyking.com/hobbyking/store/__66719__Turnigy_9XR_PRO_Radio_Transmitter_Mode_1_without_module_US_Warehouse_.html) Ok so this looks like the platform of choice to enter open source control

Note that with this platform you still need a TX module to stick in the controller that actually does the transmissions
[OpenLRS](http://openlrsng.org/) seems to be the leader in this field.  They have a great [hardware list](http://openlrsng.org/#hardware) on their site.  Here's a few suggestion on HobbyKing:
* [OrangeRX TXmodule 100Mw](http://www.hobbyking.com/hobbyking/store/__27095__OrangeRx_Open_LRS_433MHz_TX_Module_100mW_JR_Turnigy_compatible_.html)
* [OrangeRX TXmodule 1W](http://www.hobbyking.com/hobbyking/store/__43852__OrangeRX_Open_LRS_433MHz_Transmitter_1W_JR_Turnigy_Compatible_.html)

### Radio RX

Then you'll need a module inside your UAV to receive your transmissions to control the craft.
[OpenLRS](http://openlrsng.org/) seems to be the leader in this field.  They have a great [hardware list](http://openlrsng.org/#hardware) on their site.  
You can find the [hawkeye](http://www.amazon.com/DTF-UHF-MiniRX-OpenLRSng-Receiver/dp/B00QBKZI00) on amazon there, or 
the [OrangeRx](http://www.hobbyking.com/hobbyking/store/__27096__OrangeRx_Open_LRS_433MHz_9Ch_Receiver.html) at hobbyking there

### UAV Frame, batteries, motors, and ESPs

Now we need the drone itself, I'm a big fan of starting small and going big later so let's look at a few of the '200' class (200 mm that is), 
you will also need at least four motors (start with a quad as hexcopters are more complicated),
four electronic speed controllers (ESPs),
one battery (2s - for 2 cells in series, you can break your equipment later by trying a 3s)
don't forget propellors!


[qav180](http://www.getfpv.com/multi-rotor-frames/qav180-qav210-mini-fpv-quad/qav180-carbon-fiber-fpv-quadcopter.html)

and a sub$20 hobbyking frame [here](http://www.hobbyking.com/hobbyking/store/__85254__Diatone_Blade_200_Class_Micro_Multirotor_Frame_Kit.html)
notice you can choose parts that go with it below.

or there are whole kits on [amazon](http://www.amazon.com/dp/B010FMGUS8?psc=1)

notice that still needs the radio like the 9Xr above

###Highlights from HobbyKing 2015 Beer Lift Challenge
[youtube video here](https://www.youtube.com/embed/Lh5Jbi6AcsE)

### Taking it Further with FPV

The next step is to get yourself a tiny camera attach it to your drone and connect it's output to a tiny transmitter on your drone.  From which you'll broadcast a live video feed of your drone flying around, I'm going to shop these systems and post at a later date my conclusions

for now check out [GetFPV](http://www.getfpv.com/) and [HobbyKing](http://www.hobbyking.com/) both for large selections of equipment

Eventually I want to hook a flight stick up instead of having to use the little RC sticks [forum topic talking about USB input](http://openrcforums.com/forum/viewtopic.php?t=6538)

Happy Droning folks!
