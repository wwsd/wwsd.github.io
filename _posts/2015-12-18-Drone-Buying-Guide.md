---
title: Build your own Drone
description: Why pay lots of money for a toy you KNOW you are going to break?
published: true
layout: post
disqus: yes
fbcomments: no
category: embedded
tags:
  - arduino
  - drone
  - openpilot
---

Why pay lots of money for a toy you KNOW you are going to break?
Instead let's build our own so we know we can repair it easily and cheaply, 
plus we'll get to choose our own components, and later on when we want to scale up we can just remove the brains,
build a new frame, place brains inside, and attach bigger motors!  Moar power!  Mwahahahahahahah!

### Pilot Software

Let's start with the brains of the matter, there are quite a few choices out there,
I'm going to stick to the open source stuff so we can hack on it.

[Ardupilot](http://ardupilot.com/) is a nice place to start, 
take a robot add an arduino and you got yourself an autonomous pet to do your bidding.
They also made the [Mission Planner](http://planner.ardupilot.com/) software you'll see everywhere.
They are related to [diydrones](http://diydrones.com/) who claim to be the largest community of UAV amateurs, and by all means its a great place to discuss these things

[pixhawk](https://pixhawk.org/choice) seems to be a popular choice albeit with dedicated hardware 
and bit higher of a price this seems to be an up and coming feature rich option

[AeroQuad](http://aeroquad.com/content.php) This project includes some hardware designs as well as software which you can find on [github](https://github.com/AeroQuad/AeroQuad/)

[NG-UAVP](http://ng.uavp.ch/FrontPage) Autonomous flight with an emphasis on aerial photography

[Paparazzi](http://wiki.paparazziuav.org/wiki/Main_Page) has been around for awhile, it’s focus is on autonomous flying.

[DroneCode](https://www.dronecode.org/)  is a consortium with an impressive [memeber list](https://www.dronecode.org/about/project-members) this project is composed of many smaller projects, some of which I have already mentioned, you can find them all [here](https://www.dronecode.org/dronecode-software-platform)

[Open Pilot](https://www.openpilot.org/) is yet another open software group dedicated to drone pilot software and hardware. The [CC3D](http://amzn.to/1OcADR6) is one of the cheaper pieces of hardware available to pilot your drone. And is my recommendation for your first drone

### Radio TX

Every RC enthusiast needs a big honking Radio Controller to shout to the world about their nerdliness.
Beware of the ultra cheap stuff, like this Hobby King 
[4ch TX and RX](http://www.hobbyking.com/hobbyking/store/__8337__Hobby_King_2_4Ghz_4Ch_Tx_Rx_V2_Mode_1_.html).
That will not drive all the channels necessary for our flight apparatus.
But you also don't need an expensive [Futaba 18MZH](http://amzn.to/1OcAWvq)
You can find some really cool retro stuff out there like this
[Taranis X9E](http://www.hobbyking.com/hobbyking/store/__87932__Taranis_X9E_Mode_2_non_EU_Version_US_Plug_.html)
That thing looks great and is expandable to 32 channels, has speech output, telemetry, all the bells and whistles
The [Taranis X9D](http://amzn.to/1OcB7qB)
is a step down but comes with the receiver module

##### 9XR

But I wanted open source so we can hack with the code.  Looking around I found that the turnigy 9x series had an open source firmware out there:
[Turnigy 9X open source firmware](http://www.instructables.com/id/Transform-a-cheap-RC-Transmitter-with-Custom-Firmw/)
Even better this had evolved into the 9XR and now has multiple different open source firmwares for it, here’s the radio:

<http://www.turnigy9xr.com/>

And now there is a 
[9XR Pro](http://amzn.to/1OcBdON)

<iframe id="viddler-d2c3680e" src="//www.viddler.com/embed/d2c3680e/?f=1&offset=0&autoplay=0&player=full&secret=58779214&disablebranding=0&view_secret=49636673" width="545" height="349" frameborder="0" scrolling="no" allowfullscreen></iframe>

Ok so this looks like the platform of choice to enter open source control

Note that with this platform you still need a TX module to stick in the controller that actually does the transmissions
[OpenLRS](http://openlrsng.org/) seems to be the leader in this field.  They have a great [hardware list](http://openlrsng.org/#hardware)
on their site.  Here is a few suggestions on:
* [OrangeRX TXmodule 100Mw](http://www.hobbyking.com/hobbyking/store/__27095__OrangeRx_Open_LRS_433MHz_TX_Module_100mW_JR_Turnigy_compatible_.html)
* [OrangeRX TXmodule 1W](http://www.hobbyking.com/hobbyking/store/__43852__OrangeRX_Open_LRS_433MHz_Transmitter_1W_JR_Turnigy_Compatible_.html)

### Radio RX

Then you'll need a module inside your UAV to receive your transmissions to control the craft.
Again [OpenLRS](http://openlrsng.org/) seems to be the leader in this field.
They have a great [hardware list](http://openlrsng.org/#hardware) on their site.
You can find the [hawkeye](http://astore.amazon.com/joshuacoxgith-20/detail/B00QBKZI00) on amazon there, or 
the [OrangeRx](http://www.hobbyking.com/hobbyking/store/__27096__OrangeRx_Open_LRS_433MHz_9Ch_Receiver.html) at hobbyking there

### UAV Frame, batteries, motors, and ESPs

Now we need the drone itself, I'm a big fan of starting small and going big later so let's look at a few of the '200' class (200 mm that is), 
there is a sub$20 frame [here](http://amzn.to/1NXM5UU),
you will also need at least four motors (start with a quad as hexcopters are more complicated),
four electronic speed controllers (ESPs),
one battery (2s - for 2 cells in series, you can break your equipment later by trying a 3s)
don't forget propellors!

or there are whole kits on [amazon](http://amzn.to/1mcJmwm) and that one is eligible for Amazon prime meaning you can get 2-day shipping for free, just in time for Christmas! That one is the cheapest, there are a few more on there as well that come with bigger frames etc that you can find [here](http://astore.amazon.com/joshuacoxgith-20)

notice that any of those still need the radio like the [9XR Pro](http://amzn.to/1OcoHPt) that I mentioned above.

###Highlights from HobbyKing 2015 Beer Lift Challenge

HobbyKing has some great challenges where they ask RC operators to do some pretty cool stuff, here are the highlights from the 2015 Beer Lift Challenge.
<iframe width="560" height="315" src="https://www.youtube.com/embed/Lh5Jbi6AcsE" frameborder="0" allowfullscreen></iframe>

### Taking it Further with FPV

The next step is to get yourself a tiny camera attach it to your drone and connect it's output to a tiny transmitter on your drone.  From which you'll broadcast a live video feed of your drone flying around, I'm going to shop these systems and post at a later date my conclusions

for now check out [GetFPV](http://www.getfpv.com/) and [HobbyKing](http://www.hobbyking.com/) both for large selections of equipment

Eventually I want to hook a flight stick up instead of having to use the little RC sticks [forum topic talking about USB input](http://openrcforums.com/forum/viewtopic.php?t=6538)

I’m setting up an [amazon store](http://astore.amazon.com/joshuacoxgith-20) with a bunch of this collected in one location.  Mainly so I can help others do the same thing with their blogs.  Happy Droning folks!

