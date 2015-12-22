---
layout: post
title: Proseio as CMS
published: true
disqus: true
fbcomments: false
category: jekyll
tags: 
  - jekyll
  - proseio
photo_url: /img/proseio.svg
---


Proseio as CMS
![](/img/proseio.svg)

Ok, so let’s talk about [Prose.io](http://prose.io/) an amazing service from  [Development Seed](http://developmentseed.org)

This gives an easy to use graphical user interface to jekyll blogs and many other static sites.  I will suggest a few tweaks. First if you’ll configure prose like I describe in my blog post here:

[joshuacox.github.io/jekyll/2015/12/04/Prose-Configuration](http://joshuacox.github.io/jekyll/2015/12/04/Prose-Configuration/)

This makes your metadata easily editable with checkboxes and dropdown forms, 
it will also limit prose to only letting you edit things in the `_posts` folder and `_drafts`,
this keeps things very simple, where someone who does not know html at all can easily write nicely formatted posts 
with headings pictures and embedded videos without issue.

My favorite thing about this editor is that behind the scenes it is actually using git,
so that someone who has no knowledge of what ‘git’ is can easily make ‘commits’
and push content into git without even knowing a single thing about the command line or plain text editors.
Though I’d recommend you at least learn how to make headings and add links and images from my blog post here:

[0-to-60-in-Markdown](http://joshuacox.github.io/jekyll/2015/12/02/0-to-60-in-Markdown/)

it is important to note that you can run this yourself as they have source code available here:

[https://github.com/prose/prose/](https://github.com/prose/prose/)

This ensures that we will be able to run our own in the future! Let's see a demo of ProseIO in action on this very blog, this very post in fact:

<iframe width="560" height="315" src="https://www.youtube.com/embed/BfbMmj_xZ4k" frameborder="0" allowfullscreen></iframe>

There is a great fedoss episode on Jekyll being used for healthcare.gov here:

[fedscoop.com/fedoss-jekyll-prose-github-and-healthcare-gov](http://fedscoop.com/fedoss-jekyll-prose-github-and-healthcare-gov/)

And the blog post from Development seed themselves here:

[developmentseed.org/blog/new-healthcare-gov-is-open-and-cms-free](https://developmentseed.org/blog/new-healthcare-gov-is-open-and-cms-free/)

#### Taking it further

Well I would suggest looking into the next topic which is WYSIWYG

### WYSIWYG

First I point you to this post:
[https://github.com/prose/prose/issues/139](https://github.com/prose/prose/issues/139)

And the substance of the issue [Subtance.io](http://substance.io/)

Ok let's hope that issue 139 results in complete WYSIWYG integration, until then let's enjoy prose.io for what it is
