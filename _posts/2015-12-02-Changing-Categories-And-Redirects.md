---
title: Changing Jekyll Categories And Redirects
published: true
layout: post
disqus: yes
fbcomments: no
category: jekyll
description: Who gets the category right the first time around?
tags: 
  - jekyll
---

Who gets the category right the first time around?  

I certainly never seem to, and it’s always right after I share the link on some sort of social media, so I know hits wil be coming at the old address.

So let’s use the jekyll-redirect-from plugin (one of the few available on github pages)

You’ll need to add this to your `_config.yml`

{% raw  %}
    gems:
      - jekyll-redirect-from
{% endraw  %}

then in the front matter of the post that is changing category add a `redirect_from` (replace OLD_CATEGORY with the name of your OLD_CATEGORY, I tend to just copy the URI from the post before I change the category )

{% raw  %}
    redirect_from:
      - /OLD_CATEGORY/2015/11/28/POST_NAME.html
      - /OLDER_CATEGORY/2015/11/28/POST_NAME.html
{% endraw  %}

Now people will get a metarefresh when they visit the old URL

You can see the official docs from github on this subject here:

[Github help page for redirects] https://help.github.com/articles/redirects-on-github-pages/
