---
published: false
layout: post
title:  "Investigation Records for Security Operations"
summary: "This article provides guidance on how to document a case in security operations. When you triage security events, investigate something suspicious, or respond to an incident, what you record is important. It provides evidence that your investigation was thorough, accurate, and correct. For complicated incidents, your notes support your team. They also allow others to learn from your past work."
authors: [michael]
categories: [Blog]
image: assets/images/case-management.png
tags: [secops,security-operations,documentation,writing,case-management,incident-reporting,case-notes]
date: 2025-02-23 19:00:00
---
{{ page.summary }}[^1]

# Introduction

# Definitions
I will use the terms from Splunk Enterprise Security 8.0, which is aligned to the Open Cybersecurity Schema Framework (OCSF)[^2]:

Threat
: A Threat is a potential occurrence that could cause harm to an organization’s assets. These are the events we are investigating.
Findings
: Investigation
xxxxx
Incident
: An Incident is an occurrence that has caused or may cause harm to an organization’s assets. We still call it an incident even when impact has not occurred. Actions we take in responding to what occured may limit or prevent harm, but it is still and incident.
Events
: Events are observed occurences. For example, log files. But they may be things reported to you by email, or told to you in person or over the phone. Events describe something that occured in the world and are the basis for your findings.
Observables
: An Observable represents a specific event, action, or occurrence in the context of an investigation. Observables include IP addresses, domain names, file hashes, URLs, etc. Observables may or may not be Indicators of Compromise (IOCs).

The terms used to describe our written record of security investigations varies between organizations and specialities. You may see these term used "Case Management", "Case Notes", "Incident Record", "Evidence", "Incident Report", "Handler Diary", "Investigation" etc.

I will refer to them as "Case Notes", but I frequently say "Incident Record" and "Notes" in my day-to-day work. I refer to the actual work done to triage, identify, and contain a security event as "an investigation" or "an incident." 

# How are case notes used?

# Why do we need good case notes?

# References
[^1]: https://www.splunk.com/en_us/blog/learn/open-cybersecurity-schema-framework-ocsf.html
