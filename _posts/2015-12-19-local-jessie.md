---
title: Local Jessie for Raspberrypi ARM and the tinfoil hat sporting security nuts
published: true
layout: post
disqus: yes
fbcomments: no
category: docker
description: Create a local jessie base image from which to stem your debian based containers so they’ll work on ARM and other platforms and for increased security
tags:
  - linux
  - raspberrypi
  - docker
  - embedded
  - monitoring
  - icinga
photo_url: http://i1354.photobucket.com/albums/q698/thoth242/jessie-debian-sq_zpsj9qciuiz.jpg
---

![](http://i1354.photobucket.com/albums/q698/thoth242/debian_jessie_pic_zpsombhouiz.jpg)

Create a local jessie base image from which to stem your debian based containers so they’ll work on ARM and other platforms and for increased security.

Ok so this is a continuation of our earlier article [here](http://joshuacox.github.io/docker/2015/12/13/RaspberryPi-Docker-Cluster-Consul-Swarm/).

By starting your Dockerfiles with `FROM local-jessie` you will build images stemming from a locally produced Debian base image
built directly on the RaspberryPi itself. 
Thus ensuring not only that the image is compatible with ARM,
but perhaps more importantly it’s security as well,
because being built locally you have much more confidence in the installed packages than something built remotely.
The main project here consists of a Makefile that installs both base images on my master pi, homepage [here](http://joshuacox.github.io/local-debian/)

Essentially upon downloading that you should be able to call the script

```
./local-jessie.sh
```

afterwards you should have a local-jessie image you can source

```
root@dockerhost:~# docker images local-jessie
REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
local-jessie        latest              a651d3b45b88        2 hours ago         305.3 MB
```

and by that I mean  you can change any

```
FROM debian:jessie
```

to

```
FROM local-jessie
```

And it should use your locally built `local-jessie` from which to stem itself

An example is here where I forked the official rabbitmq image and swapped out the `FROM` line:

<https://github.com/joshuacox/rabbitmq>

Now I can use rabbitmq on my [Raspberrypi Cluster](http://joshuacox.github.io/docker/2015/12/13/RaspberryPi-Docker-Cluster-Consul-Swarm/)

If you have any problems feel to open an [issue](https://github.com/joshuacox/local-debian/issues)
