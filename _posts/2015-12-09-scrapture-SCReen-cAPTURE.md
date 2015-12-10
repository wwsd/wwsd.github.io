---
title: scrapture SCReen cAPTURE
published: true
layout: post
disqus: yes
fbcomments: no
category: cli
description: Record your desktop using avconv right from x11grab
tags: 
  - linux
  - cli
  - avconv
---

For some reason all the linux screen capture utilities are misbehaving for me at the moment, so let’s do like the title suggests and

### Record your desktop using avconv right from x11grab

Let’s try this manually:

```
avconv -video_size 1920x1080 -framerate 30 -f x11grab -i :0.0  /tmp/scrap.mp4
```

that assumes your monitor is at 1080p, but it will take a 1080p movie of your desktop as you view it. ctrl-C to kill it when you are done.

to simplify this I wrote the following script, that will automatically determine your resolution using xrandr, place the movie in a unique temporary directory, and append a line in a file for easy playing afterwards

[joshuacox.github.io/scrapture](http://joshuacox.github.io/scrapture/)

there is also a companion script that will kill the first one, careful it indiscriminately interrupts all avconv processes running under your user

Let’s see it in action:

( while the embedded iframe is still acting up I thought I’d include the link )
[Youtube link](https://youtu.be/keWlprJhECQ)

<iframe width=”560” height=”315” src=”https://www.youtube.com/embed/keWlprJhECQ” frameborder=”0” allowfullscreen></iframe>

