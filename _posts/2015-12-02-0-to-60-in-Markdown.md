---
title: 0 to 60 in Markdown
published: true
layout: post
disqus: yes
fbcomments: false
category: jekyll
description: "What is markdown?"
tags: 
  - jekyll
  - blog
---


What is markdown?

Here’s the first line under ‘philosophy’ From the [daring fireball main site](https://daringfireball.net/projects/markdown/syntax) 

“Markdown is intended to be as easy-to-read and easy-to-write as is feasible.”

Markdown is very much like an old email, you just write normally and your text is transformed into plain text between `<p></p>` tags

## Headings

you can give a header to a section by placing a `#` mark at the start of a line like so

    ## This is a title

comes out like this if I don’t indent it:

## This is a title

What was that about indenting?  Well you can tell markdown to not touch a block by placing four spaces at the start of a line, let’s see another

    ### This is an H3

And if we remove the four spaces:

### This is an H3

So placing a number of `#` in front of a line of text marks it as a heading, the more `######` the smaller the heading down to an H6

#### This is an H4

##### This is an H5

###### This is an H6

## Links

How do you add links? they are added by placing your link name inbetween square brackets, then immediately follow by your URL in parantheses like this

{% raw  %}
    [MY_LINK_NAME](http://example.com/)
{% endraw  %}

Here is an example of how I would link this blog

{% raw  %}
    [My Blog](http://joshuacox.github.io/)
{% endraw  %}

Will look like this:

[My Blog](http://joshuacox.github.io/)

## Images

How about images? Like links they are added by placing a `!` before your image name inbetween square brackets, then immediately follow by your image URL in parantheses like this

{% raw  %}
    ![IMAGE_TITLE](PICTURE_URL)
{% endraw  %}

So if you place an image in the `img` folder in your site you could call it like so:

{% raw  %}
    ![My helpful screenshot]({{ site.url }}/img/screenshot.jpg)
{% endraw  %}

To learn more I suggest you read the daring fireball main site:

[https://daringfireball.net/projects/markdown/](https://daringfireball.net/projects/markdown/)

of course the basics page is a good page for those starting out

[https://daringfireball.net/projects/markdown/basics](https://daringfireball.net/projects/markdown/basics)

Enjoy!
