---
title: Prose Configuration
published: true
layout: post
disqus: yes
fbcomments: no
category: jekyll
description: Once you configure prose it becomes much more user friendly.
tags: 
  - jekyll
  - proseio
redirect_from:
  - /blog/2015/12/04/Prose-Configuration/
---

Once you configure prose it becomes much more user friendly.  So let’s add some lines to our `_coonfig.yml` and improve our user’s experience.

First, if you have not, check out the getting started page:

[github.com/prose/prose/wiki/Getting-Started](https://github.com/prose/prose/wiki/Getting-Started)

There’s a pretty good introduction to all this and they point out a sample config, I started with the starter config here:

[github.com/prose/starter/blob/gh-pages/_config.yml](https://github.com/prose/starter/blob/gh-pages/_config.yml)


First you need the baseurl of your site, we’ll set the permalinks to pretty and use the rdiscount markdown engine

{% raw  %}
      baseurl: /
      permalink: pretty
      markdown: rdiscount
{% endraw  %}

Rdiscount is worthy of it’s own blog post, but for now I’ll give a link:

[dafoster.net/projects/rdiscount](http://dafoster.net/projects/rdiscount/)

Now let’s introduce the specific prose configurations, first you begin with a `prose:` block, we’ll set the root url for prose to `_posts` meaning that prose will only work with files in the `_posts` folder ( and `_drafts` )

{% raw  %}
    prose:
      rooturl: '_posts'
{% endraw  %}

Then we set our siteurl and point to our relativelinks json file

{% raw  %}
      siteurl: 'http://joshuacox.github.io/'
      relativeLinks: 'http://joshuacox.github.io/links.jsonp'
{% endraw  %}

Then we tell prose to place uploads into the `media` folder, this enables people to use the fantastic image uploader from prose

{% raw  %}
      media: 'media'
{% endraw  %}

Now we’re going to set some default metadata and tell prose what to expect from users to set up their  posts

{% raw  %}
    metadata:
      _posts:
        - name: "layout"
          field:
            element: "hidden"
            value: "post"
        - name: "title"
          field:
            element: "text"
            label: "Title"
            value: ""
        - name: "photo_url"
          field:
            element: "text"
            label: "450x450 Picture Thumb for index"
            value: ""
        - name: "disqus"
          field:
            element: "checkbox"
            label: "Disqus Comments"
            value: true
        - name: "fbcomments"
          field:
            element: "checkbox"
            label: "Facebook Comments"
            value: false
        - name: "published"
          field:
            element: "checkbox"
            label: "Published"
            value: false
{% endraw  %}

This next field is the categories field which will be of element type “select” meaning that you can only select one of these categories

{% raw  %}
        - name: "category"
          field:
            element: "select"
            label: "Select Category"
            placeholder: "Choose Category"
            options:
              - name: "Docker"
                value: "docker"
              - name: "Linux"
                value: "linux"
              - name: "Jekyll"
                value: "jekyll"
              - name: "CLI"
                value: "cli"
              - name: "Blog Post"
                value: "blog"
{% endraw  %}

Then there is the tags field which, unlike categories, you can select multiple, so we set the type to ‘multiselect’ and I set ‘alterable’ to true so that people can make up their own tags

{% raw  %}
        - name: "tags"
          field:
            element: "multiselect"
            label: "Add Tags"
            placeholder: "Choose Tags"
            alterable: true
            options:
              - name: "Docker"
                value: "docker"
              - name: "Linux"
                value: "linux"
              - name: "Jekyll"
                value: "jekyll"
              - name: "CLI"
                value: "cli"
              - name: "Humor"
                value: "humor"
              - name: "Ruby"
                value: "ruby"
              - name: "Javascript"
                value: "javascript"
              - name: "Python"
                value: "python"
{% endraw  %}

Let’s also set some other default metadata for anything in the `static` folder

{% raw  %}
      _posts/static:
        - name: "layout"
          field:
            element: "hidden"
            value: "page"
        - name: "title"
          field:
            element: "text"
            label: "Title"
            value: ""
        - name: "permalink"
          field:
            element: "text"
            label: "Permalink"
            value: ""
{% endraw  %}

For more info on prose configuration go here:

[github.com/prose/prose/wiki/Prose-Configuration](https://github.com/prose/prose/wiki/Prose-Configuration)

Here is my full `_config.yml` with  prose configuration all together at the bottom:

[github.com/joshuacox/joshuacox.github.io/blob/master/_config.yml](https://github.com/joshuacox/joshuacox.github.io/blob/master/_config.yml)
