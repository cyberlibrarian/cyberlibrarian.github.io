---
published: false
layout: post
title:  "Threat Hunting vs Detection Engineering"
summary: "What is the relationship between Threat Hunting and Detection Engineering? Is one part of the other? What attributes do they share? In this article I will compare several widely referenced definitions and frameworks for each. Generally, they are the same set of processes with different perspectives based on the size of the teams implementing them."
authors: [michael]
categories: [ Blog ]
tags: [detection-engineering,documentation,threat-detection,SIEM,SOAR,EDR]
---
{{ page.summary }}

# Summary

*Threat Hunting* and *Detection Engineer* are terms used to describe innovative and evolving practices for the detection of cyber-threats. The latest models for both emphasize the need for continuous development and execution (DevOps) of data sources and searches, the application statistical methods, and driven by a threat intelligence.

Differences beteween these practices are primarily driven by the need to apply these practices to different stakeholder needs. Large MSPs define successful *Threat Hunting* as generating incident response and new demand for detection engineering whose roles is create reliable high-quality automated detections from lessons learned and from more technical forms of intelligence like malware analysis. Smaller organizations where the capability to execute these practices will be concentrated into a small number of people, will not see value in distinguishing between them: they represent the same processes.

- Threat Hunting is proactive, prioritizing efforts based on based on relevance
- Detection Engineering prioritizes development by relevance and feasbility


Fallacies:

- Threat Hunting execution may trigger Incident Response, but Detection Engineering processes do not. In reality, developing a new detection rule involves the same iterative development process and examination of data as TH. Testing a detection analytic may trigger an Incident Response.

# Introduction


# Perspectives

In this section, I summarized a brief survey a number of authorative and commonly held perspectives. Some of these are *historic*: they were influential, are widely referenced, but are no longer maintained and do not represent emerging practices. For examples: SQRRL, MaGMa, and TaHiTi. Others are new and under active development from leading organizations. For examples: Splunk's PEAK and MITRE's TCHAMP. I have also included several perspective from outspoken voices. In this rapidly changing practice area, these voices are just as influential as as the organizations publishing structured frameworks. For examples, Florian Roth, Alex Texiera, . This survey is not intended to be exhaustive: it captures works that are influential on my understanding.

## SQRRL

Sqrrl added much needed structure and process to what was, until 2015, an ad-hoc activity with an "badass" name. They were purachased by Amazon Web Services in 2018 but archived copies of Sqrrl's influential framework can be found at the [Sqrrl Archive](https://www.threathunting.net/sqrrl-archive) at [The ThreatHunting Project](https://www.threathunting.net/).

"We define hunting as the process of proactively and iteratively searching through networks to detect and isolate advanced threats that evade automated, rule- and signature-based security systems.... Hunting is often machine-assisted but is always driven by an analyst; it can never be fully automated. Automated alerting is important, but cannot be the only thing your detection program relies on. In fact, one of the chief goals of hunting should be to improve your automated detection capabilities by prototyping new ways to detect malicious activity and turning those prototypes into production detection capabilities."

A memorable term introduced by Sqrrl was *Advanced Persistent Defense* to contrast with *Advanced Persistent Threat*. It emphasized the need for continuous monitoring and innovative detection methods.

## MaGMa and TaHiTI

A note of interest: one of the primary authors of MaGMa went on to work at Splunk which today offers the Splunk Security Content Library: a tool that can easily replace the MaGMa spreadsheet planning/tracking tool.

## MITRE TCHAMP

## Splunk PEAK

[The PEAK Threat Hunting Framework](https://www.splunk.com/en_us/blog/security/peak-threat-hunting-framework.html), from the SURGe by Splunk, is a recent an evolving effort to modernize *Threat Hunting*. It is informed by Sqrrl and TaHiTI, but "incorporates the additional experience and lessons... learned in the last several years."

Rather than define what Threat Hunting is, PEAK defines several types of "hunts", each with its own process, activities, and outcomes. 

- Hypothesis-Driven
- Baseline (AKA Exploratory Data Analysis or EDA)
- Model-Assisted Threat Hunts (M-ATH)

In the PEAK framework, a *Hypothesis-Driven* hunt closely matches older definitions like those from Sqrrl and TaHiTI.

Importantly, there is an overlap in PEAK's definition of Baseline and Model-Assisted hunts and emerging concepts for *Detection Engineering*. For example, Alex T.'s [Table Stakes for Detection Engineering]() argues that DE requires DevOps and Statistical methods. So does PEAK: data pipleines, baseline analysis and machine learning.

## 
