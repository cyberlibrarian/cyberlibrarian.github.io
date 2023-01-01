---
title: "The Cybersecurity Librarian"
description: "Enabling Cybersecurity Learners"
---

<!-- A list of all posts -->
<div>
{% for post in site.posts %} 
{% if post.tags contains "sticky" %}
    <h2><a href="{{site.baseurl}}{{post.url}}" class="btn btn-dark">{{post.title}}</a></h2>
    <p>
        {{ post.excerpt | strip_html | strip_newlines | truncate: 136 }}
    </p>
</div>
{% endif %}
{% endfor %}



# This is me
- <a rel="me" href="{{site.authors.michael.site}}">{{site.authors.michael.site}}</a>
- <a rel="me" href="{{site.authors.michael.github}}">{{site.authors.michael.github}}</a>
- <a rel="me" href="{{site.authors.michael.youtube}}">{{site.authors.michael.youtube}}</a>
- <a rel="me" href="{{site.authors.michael.mastodon}}">{{site.authors.michael.mastodon}}</a>
  