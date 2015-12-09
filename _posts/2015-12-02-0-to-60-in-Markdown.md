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

Markdown is very much like an old email, you just write normally and your text is transformed into plain text between `<p></p>` tags.

No clue what a `<p>` tag is?  Then markdown may be for you.

Because let’s face it, people want simple, they don’t want to know about html tags.

But they DO want to add links to their posts, and pictures, we need to add pictures, and videos, and have some big bold text for headings, and come to think of it a few different sizes of headings.

OK, how to make all that simple?  

##[Markdown](https://daringfireball.net/projects/markdown/syntax)!

It is human readable and is easy to write as well, and every now and then if you need to put some straight up HTML in there, you can do that to, but we’re not talking about that in this post.  

This is a bare knuckles guide for a first time n00b.  So let’s stick to basics.

### Links

How do you add links? they are added by placing your link name inbetween square brackets, then immediately followed by your URL in parantheses like this

{% raw  %}
    [MY_LINK_NAME](http://example.com/)
{% endraw  %}

Here is an example of how I would link this blog

{% raw  %}
    [My Blog](http://joshuacox.github.io/)
{% endraw  %}

Will look like this:

[My Blog](http://joshuacox.github.io/)

### Images

How about images? Like links they are added by placing a `!` before your image name inbetween square brackets, then immediately followed by your image URL in parantheses like this

{% raw  %}
    ![IMAGE_TITLE](PICTURE_URL)
{% endraw  %}

So if you place an image in the `img` folder in your site you could call it like so:

{% raw  %}
    ![My helpful screenshot]({{ site.url }}/img/screenshot.jpg)
{% endraw  %}

### Headings

you can give a header to a section by placing a `#` mark at the start of a line like so

    ### This is a title

comes out like this if I don’t indent it:

### This is a title

What was that about indenting?  Well you can tell markdown to not touch a block by placing four spaces at the start of a line, let’s see another

    #### This is an H4

And if we remove the four spaces:

#### This is an H4

So placing four spaces at the beginning of a line tells jekyll to ignore the next block and make it as `code`,  that way I can show you `#` beginning at the start of a line withoput it turning it into a heading.  

Again a number of `#` in front of a line of text marks it as a heading, the more `######` the smaller the heading down to an H6

# This is an H1

## This is an H2

### This is an H3

#### This is an H4

##### This is an H5

###### This is an H6

And this is regular text, which you just type normally without starting the line with four spaces or `#` marks.  That is the basics.

## Going further

To learn more I suggest you read the daring fireball main site:

[https://daringfireball.net/projects/markdown/](https://daringfireball.net/projects/markdown/)

of course the basics page is a good page for those starting out

[https://daringfireball.net/projects/markdown/basics](https://daringfireball.net/projects/markdown/basics)

Enjoy!
