---
title: disqus-and-jekyll
published: true
layout: post
og_image_url: 
disqus: yes
comments: no
tags: [joshuacox, blog]
---

Using jekyll with disqus is quite easy, you merely need to add some lines to your `_layouts/post.html`, here’s what I did:

1. First add this right after your body tag (where DISQUS_SITE_NAME is the name you gave disqus for this particular site):
```
    {% if page.disqus %}
      <script id="dsq-count-scr" src="//DISQUS_SITE_NAME.disqus.com/count.js" async></script>
    {% endif %}
```


2. Then add this somewhere after your content block  (where DISQUS_SITE_NAME is the name you gave disqus for this particular site, and DISQUS_URL is the actual URL for your site):
```
  {% if page.disqus %}
      <div id="disqus_thread"></div>
      <script>
      /**
      * RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
      * LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables
      */
      var disqus_config = function () {
      this.page.url = "http://DISQUS_URL{{ page.url }}"; // Replace PAGE_URL with your page's canonical URL variable
      this.page.identifier = "DISQUS_URL{{ page.url }}"; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
      };
      (function() { // DON'T EDIT BELOW THIS LINE
      var d = document, s = d.createElement('script');

      s.src = '//DISQUS_SITE_NAME.disqus.com/embed.js';

      s.setAttribute('data-timestamp', +new Date());
      (d.head || d.body).appendChild(s);
      })();
      </script>
      <noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
    {% endif %}
```

Now make a post with this line in the YAML front matter:
```
disqus: yes
```
and you should be good to go.  Testing at the bottom of this post in fact
