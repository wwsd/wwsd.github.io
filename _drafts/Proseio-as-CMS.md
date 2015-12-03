---
title: Proseio as CMS
published: true
layout: post
disqus: yes
fbcomments: no
category: jekyll
tags: 
  - jekyll
  - proseio
photo_url: /img/proseio.svg
---

title: Proseio as CMS
![](/img/proseio.svg)

Ok, so let’s talk about [Prose.io](http://prose.io/) an amazing service from github themselves

it is important to note that you can run this yourself as github have source code available here:

[https://github.com/prose/prose/](https://github.com/prose/prose/)

### Config
{% raw  %}
    defaults:
      -
        scope:
          path: "" # an empty string here means all files in the project
          type: "posts" # previously `post` in Jekyll 2.2.
        values:
          layout: "post"
          disqus: true
          category: blog
          tags:
            - blog
{% endraw  %}
