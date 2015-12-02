---
title: Jekyll Default Configs
published: true
layout: post
disqus: yes
fbcomments: no
category: jekyll
tags: 
  - jekyll
---

Let’s add some default configs to jekyll so that when people add a new post without the YAML front matter it will still get a default layout etc

### Scope

First there is the path portion of the scope we are going to leave this one wide open 

{% raw  %}
        path: "" # an empty string here means all files in the project
{% endraw  %}

Then we will restrict to posts

{% raw  %}
        type: "posts" # previously `post` in Jekyll 2.2.
{% endraw  %}

# Values

Then you’ll need to add in some default values this is what you usually put in your YAML front matter, I set a default layout of `post`, I set disqus to true to include commenting, and I set the category and tags to default to ‘blog’

{% raw  %}
      layout: "post"
      disqus: true
      category: blog
      tags:
        - blog
{% endraw  %}

### Final Config

Here is the final default config I am using for this site

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


for more in-depth documentation refer to the [Jekyll Configuratio docs](http://jekyllrb.com/docs/configuration/)
