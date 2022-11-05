---
title: "Michael McDonnell"
layout: default
permalink: "/author-michael"
---
<div class="container">
<div class="row justify-content-center">
    <div class="col-md-8">
        <div class="row align-items-center mb-5">
            <div class="col-md-9">
                <h2 class="font-weight-bold">{{page.title}}<span class="small btn btn-outline-success btn-sm btn-round"><a href="{{site.authors.michael.twitter}}">Follow</a></span></h2>
                <p><a rel="me" href="{{site.authors.michael.site}}">{{site.authors.michael.site}}</a></p>
                <p><a rel="me" href="https://youtube.com/c/cyberlibrarian">https://youtube.com/c/cyberlibrarian</a></p>
                <p><a rel="me" href="https://github.com/cyberlibrarian">https://github.com/cyberlibrarian</a></p>
                <p><a rel="me" href="https://infosec.exchange/@cyberlibrarian">https://infosec.exchange/@cyberlibrarian</a></p>
                <p class="excerpt">{{site.authors.michael.bio}}</p>
            </div>
            <div class="col-md-3 text-right">
                <img alt="{{site.authors.michael.name}}" src="{{site.baseurl}}/{{site.authors.michael.avatar}}" class="rounded-circle" height="100" width="100">
            </div>
        </div>
        <h4 class="font-weight-bold spanborder"><span>Posts by {{page.title}}</span></h4>
            {% assign posts = site.posts | where:"authors","michael" %}
            {% for post in posts %}
            {% include main-loop-card.html %}
            {% endfor %}
    </div>
</div>
</div>
