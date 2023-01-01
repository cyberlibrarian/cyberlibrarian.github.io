---
title: "Moro and Mike"
permalink: "/moro-and-mike/about"
---
"Moro and Mike" was a weekly livestream discussing the cybersecurity profession practice. Our topics included leadership, management, job hunting, career development, emotional intelligence, threat intelligence, situational awareness and more. We go beyond the technology to discuss the professional practice of cybersecurity and IT.
		
## Podcasts

Moro and Mike is recorded live on YouTube, but past episodes are available in podcast (audio-only) format on:
- [YouTube](https://youtube.com/cyberlibrarian/)
- [iTunes](https://podcasts.apple.com/ca/podcast/moro-and-mike/id1523514571)
- [Spotify](https://open.spotify.com/show/0YK3VLKedbZ3YZyj33v7Cq?si=PtWdFp3ATJ21jhnp3TRvdw), 
- and [Google Podcasts](https://podcasts.google.com/feed/aHR0cHM6Ly93d3cuY3liZXJsaWJyYXJpYW4uY2EvbW9yby1hbmQtbWlrZS9wb2RjYXN0LnJzcw?sa=X&ved=0CAYQrrcFahcKEwi4zImFw-TqAhUAAAAAHQAAAAAQAQ)

Just search for "Moro and Mike".

## Past Livestreams
{% assign posts = site.posts | where:"categories","Moro and Mike" %}
{% for post in posts %}
{% if post.title != null %}
{% if group == null or group == post.group %}         
- [{{ post.title }}]({{ post.url | relative_url }})
{% endif %}
{% endif %}
{% endfor %}
{% assign posts = nil %}
{% assign group = nil %}
