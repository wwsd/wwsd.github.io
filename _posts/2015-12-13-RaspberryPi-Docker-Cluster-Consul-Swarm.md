---
title: RaspberryPi Docker Cluster Consul Swarm
published: true
layout: post
disqus: yes
fbcomments: no
category: docker
description: build a raspberrypi docker swarm cluster with ease repeatably
tags: 
  - linux
  - docker
  - swarm
  - cluster
  - consul
photo_url: http://i1354.photobucket.com/albums/q698/thoth242/hypriot_zpsqhyizsex.png
---

### Build a RaspberryPi docker swarm cluster repeatably with ease

This one is very cool, you end up with a personal cloud built in RaspberryPi2s that balances the containers amongst your swarm automatically, and because the nodes are autodetected and automagically added to the cluster this can be done in less than thirty minuters assuming you have everything

![](http://i1354.photobucket.com/albums/q698/thoth242/hypriot_zpsqhyizsex.png)

The old raspberrypi1s were pretty cool, but the 2nd generation demands attention with quad-core processors and 1GB of RAM at $40 you can build a cluster of computing hardware that is pretty cheap to get started, and easy to scale.  Just add more $40 nodes

##### Requirements

* 2 or more raspberrypis (2 preferred for the quad-core and 1GB of RAM, though you can use the previous RaspberryPi as well [so long as it has a network port or wifi dongle])
* 2 microSD cards
* 1 network

![](http://i1354.photobucket.com/albums/q698/thoth242/cluster_lab_zpssjdhfbrv.png)

OK first, I started here: [blog.hypriot.com/post/introducing-hypriot-cluster-lab-docker-clustering-as-easy-as-it-gets/](http://blog.hypriot.com/post/introducing-hypriot-cluster-lab-docker-clustering-as-easy-as-it-gets/)

I then forked their flash repo and added a Makefile: [joshuacox/hypriot-flash](https://github.com/joshuacox/hypriot-flash)

###### NOTE: Everything from here on is a repeat of above the hypriot blog post but utilizing my makefile for repeatability, please run through the hypriot blogpost first so that you are familiar with the process before using the makefile

### Makefile usage

First stick the SDCARD in, then use `dmesg` to ensure that it is `/dev/mmcblk0` you’ll see some lines like the following in the dmesg

```
[13943.322789] mmcblk0: mmc0:e624 SU16G 14.8 GiB 
[13943.331703]  mmcblk0: p1 p2
[14383.049094]  mmcblk0: p1 p2
```

##### Master

Now flash your master node, you will be prompted for details

```
make master
```

Then take out the sd card and put it in your master raspberrypi, plug it into your network, and power it on

##### Node1

plug in your second SD card and make a subordinate node, if you have more cards repeat giving unique node names for each node

```
make node
```

Alternatively make a wifi enabled node, giving wifi details as prompted for them

```
make wifi
```

Power the node(s) on

#### KeyMaster

by now you should be able to key the master node with your ssh keys, ( you can do this manually with ssh-copy-id ) the password will be ‘hypriot’

```
make key
```

Now enter the master node with `make enter` which will ssh you into the master pi that you just keyed, and change the password with the `passwd` utility

```
make enter
```

then raise the ui

```
make ui
```

Gaze upon all the wonderment

```
make show
```

This last one requires your BROWSER environmnet variables to be set, something like this in `.bashrc` or similar for your shell of choice

```
export BROWSER=chromium
```

Now create the overlay

```
make overlay
```

And test the overlay

```
make overlay-test
```

you should now be able to create more containers at will and they will distribute among your cluster

#### Helper scripts

###### Roustabout

is my answer to a few shortcuts that should be there by default,
especially `LastDocker` which will execute a bash shell in the last docker container started, also see it’s sister `LogDockerLast`
more details here [joshuacox.github.io/roustabout](http://joshuacox.github.io/roustabout/)

###### Local base images

From here may I suggest you add some local base files from which to build.
By starting your Dockerfiles with `FROM local-alpine` or `FROM local-jessie`
which will build images locally for [Alpine](http://www.alpinelinux.org/) and [Debian](https://www.debian.org/) respetively,
you will be able to stem from images you buid directly on the RaspberryPi itself.
Thus ensuring not only that the image is compatible with ARM, but perhaps more importantly
it’s security as well, because being built locally you have much more confidence 
in the installed packages than something built remotely.  I have a script that installs both base images on my master pi here: [http://joshuacox.github.io/local-base/](http://joshuacox.github.io/local-base/)

Now what that does is download two other repos, and build the two base images:

[http://joshuacox.github.io/local-debian/](http://joshuacox.github.io/local-debian/)

[http://joshuacox.github.io/local-arm/](http://joshuacox.github.io/local-arm/)

As I find more local build scripts for base images I intend on adding them to local-base so that there a broad spectrum of hosts I can build in ARM securely

#### Bocker vs. Clucker

Ok so this is a tough one, if applied to the [bokbot](http://bokbot.com/), is this a

bocker  ~or~  clucker
