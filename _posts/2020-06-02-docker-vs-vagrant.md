---
layout: post
title:  "Kali Linux in Docker"
authors: [michael]
categories: [ Technical Tuesday ]
image: assets/images/2020-06-02.png
youtube: 62Yt-AU-2Dc
tags: [docker,vagrant,ansible,livestream]
---
In this livestream I will show how I run Kali Linux in a Docker Container on Docker for Windows. It helps me get the best of both worlds, and I don't need to maintain a VM.

I will be joined by Neil Stewart who will explain how he does similar tasks using VMs with Vagrant and Ansible, and we will discuss a comparison of the two methods.

Even better, when I have to custom compile a tool for security assessment or adversary simulation, I an build a container for just one tool and not worry about breaking my other Kali tools.

I will show:

-how to quickly run kali commands without interacting with the underlying linux OS
-how to move data to/from your windows folders
-how to make a customer Kali-based container when you want a pre-built container with custom tools and programs

[![thumbnail for {{page.title}} youtube video]({{page.image | relative_url}})](https://youtu.be/{{page.youtube}} "{{page.title}}")
