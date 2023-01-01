---
title: "The Cybersecurity Librarian"
description: "Enabling Cybersecurity Learners"
---
# Posts
{% for post in site.posts %} 
{% if post.tags contains "sticky" %}
## [{{post.title}}({{site.baseurl}}{{post.url}})]
{{ post.excerpt | strip_html | strip_newlines | truncate: 136 }}
{% endif %}
{% endfor %}

# This is me
- <a rel="me" href="{{site.authors.michael.site}}">{{site.authors.michael.site}}</a>
- <a rel="me" href="{{site.authors.michael.github}}">{{site.authors.michael.github}}</a>
- <a rel="me" href="{{site.authors.michael.youtube}}">{{site.authors.michael.youtube}}</a>
- <a rel="me" href="{{site.authors.michael.mastodon}}">{{site.authors.michael.mastodon}}</a>
  