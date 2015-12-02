---
title: Jekyll Debug
published: true
layout: post
disqus: yes
fbcomments: no
debugger: false
description: Let’s pick apart Jekyll’s brain today
category: jekyll
tags: 
  - jekyll
redirect_from:
  - /blog/2015/12/02/Jekyll-Debug.html
---

Let’s pick apart Jekyll’s brain today

I asked this question at Stack Overflow and got a fantastic response very quickly:

[Stack Overflow Question](http://stackoverflow.com/questions/34048313/jekyll-debug-or-print-all-variables)

First you have make a new directory `_plugins` if you don’t already have one, then add a debug.rb into it:

{% raw  %}
    Let’s implement this in our blog
    # A simple way to inspect liquid template variables.
    # Usage:
    #  Can be used anywhere liquid syntax is parsed (templates, includes, posts/pages)
    #  {{ site | debug }}
    #  {{ site.posts | debug }}
    #
    require 'pp'
    module Jekyll
      # Need to overwrite the inspect method here because the original
      # uses < > to encapsulate the psuedo post/page objects in which case
      # the output is taken for HTML tags and hidden from view.
      #
      class Post
        def inspect
          "#Jekyll:Post @id=#{self.id.inspect}"
        end
      end
      
      class Page
        def inspect
          "#Jekyll:Page @name=#{self.name.inspect}"
        end
      end
      
    end # Jekyll
      
    module Jekyll
      module DebugFilter
        
        def debug(obj, stdout=false)
          puts obj.pretty_inspect if stdout
          "<pre>#{obj.class}\n#{obj.pretty_inspect}</pre>"
        end

      end # DebugFilter
    end # Jekyll

    Liquid::Template.register_filter(Jekyll::DebugFilter)
{% endraw  %}

Then I like to make an include file in it I place a div containing that `{% raw  %}{{ site | debug }}{% endraw  %}` like so

{% raw  %}
    <div class="debugger">
      <div class="container text-center">
        sitedebug
        {{ site | debug }}
      </div><!--//container-->
    </div><!--//div-->
{% endraw  %}

Then inside your `_layouts/post.html` you conditionally call your debug block:

{% raw  %}
    {% if page.debugger %}
      {% include debugger.html %}
    {% endif %}
{% endraw  %}

Then in the front matter of a post turn it on:

     debugger: true

And Jekyll will dump the contents of it’s brain onto your page

I find this useful for making sure everything is set as it is supposed to be, and it is useful for finding out about variables you did not know about

Happy Debugging!
