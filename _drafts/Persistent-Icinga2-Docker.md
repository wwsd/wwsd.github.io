---
title: Persistent Icinga2 Docker on RaspberryPi Cluster
published: true
layout: post
disqus: yes
fbcomments: no
category: blog
description: Icinga2 is a next gen fork of Nagios, to continue playing with it you might want a little bit of persistence
tags: 
  - linux
photo_url: /img/thumbs/icinga_logo.jpg
---

![](/img/icinga_logo.jpg)

[Icinga2](https://www.icinga.org/icinga/icinga-2/) is a next gen fork of [Nagios](https://www.nagios.com/).  
Whereas while using the open source base from the organization [Nagios](https://www.nagios.org/) you always felt like you were missing out
by not paying your dues to Nagios Enterprise. Along came Icinga a fork with much of the features offered by the enterprise version of nagios 
for free.  It was open source and all the plugins still worked.  So repositories of generic plugins like this [one](https://www.monitoring-plugins.org/)
did not go to waste.  But with the second version they really upped the ante, the full feature list is [here](https://www.icinga.org/icinga/icinga-2/features/).  
Some of the most impressive improvements are in the clustering area.  Well that makes it a great candidate for dockerization.  

Let’s use ansible to spin up a docker container I have a previous [post](http://joshuacox.github.io/docker/2015/11/28/Icinga2-Docker/) 
on this topic, but I felt the other methods were failing me and I wanted more persistence

I started trying to convert the official container into a persistent instance with [mkicinga](https://github.com/joshuacox/mkicinga), 
however, mysql was acting funny on me, and I’d rather not have it in the image anyhow, so I went back to the fork of jeyk’s old debian based [Dockerfile](http://joshuacox.github.io/docker-icinga2)

#### Requirements

* [RaspberryPi Full kit](http://astore.amazon.com/joshuacox-20/detail/B00MV6TAJI/189-3117811-4891539) at least one, but I’d recommend three
* [Cluster setup](http://joshuacox.github.io/docker/2015/12/13/RaspberryPi-Docker-Cluster-Consul-Swarm/) from our previous post there

#### Usage

should be easy first pull the temporary recipe up

```
make temp
```

Let it finish populating the databases, (you can watch by using `make logs` ctrl-c to exit viewing the logs, despite what the warning says you will actually not kill the container
[because your are killing the `tail -f` of the log watching process not the process itself in this case])
and `killall mysql`


```
make enter      # we have ‘entered’ the container
killall mysql   # note this is ran inside of the container
exit            # back in the host environment now
```


then grab all the persistent volumes

```
make grab
```

then run in `prod` mode, take this ‘prod’ with a grain of salt, I’ll leave it to you to understand all security implications of the 
MYSQL_ROOT_PASS file hanging out after these Makefiles have ran (i.e. on all docker machines you should implicitly trust all users with the ‘docker’ group as they effectively have root on the machine)

```
make prod
```

again main page here for it:

[joshuacox.github.io/docker-icinga2](http://joshuacox.github.io/docker-icinga2)

{% raw  %}
{% endraw  %}
