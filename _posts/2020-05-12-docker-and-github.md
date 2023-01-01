---
title:  "Docker and Github"
authors: [michael]
categories: [ Technical Tuesday ]
image: assets/images/2020-05-12.png
youtube: -JdsAC7heks
tags: [docker,github,devops]
---
Recently I started to use Docker and Github together to build and deploy analysis projects with a single command line. To do this, I setup a github repository with my Dockerfile (build instructions) and upload data and scripts needed for my analysis. 

Whenever I want to perform the analysis, I simply run a single command on my Windows workstation. It builds my container, runs it, passes parameters, and exits when the analysis is done. 

This allows me to re-use my containers and easily create new analysis experiments simply by creating a new repository.

In this livestream I will walk through my use cases and how I use docker step-by-step.

[![thumbnail for {{page.title}} youtube video]({{page.image | relative_url}})](https://youtu.be/{{page.youtube}} "{{page.title}}")
