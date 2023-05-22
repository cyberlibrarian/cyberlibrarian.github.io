---
published: false
layout: post
title:  "Are Threat Hunting and Detection Engineering the Same Thing?"
summary: "Detection Engineering is the practice of designing, developing, and maintaining systems for the detection of cyber threats. It is closely related to *Threat Hunting* and shares frameworks and processes."
authors: [michael]
categories: [ Blog ]
image: assets/images/mechanical_eye.png
tags: [detection-engineering,threat-hunting,documentation,threat-detection,SIEM,SOAR,EDR]
---
{{ page.summary }}[^1]

# Introduction

This article presents a summary of current and emerging *Detection Engineering* practices. It includes a brief history of where the term came from, and distinguishes between current practices (from the past 5 years), and those of past decades.

Modern Detection Engineering has 5 properities:
- 

# From Intrusion Detection to Detection Engineering

*Detection Engineering* (DE) is a relatively new term in cybersecurity, though the practice has evolved over decades. Related terms from past decades include *Intrusion Detection*, *Threat Detection*, *Incident Detection*, *SIEM use-case development", *Security Monitoring*, and *Threat Hunting*.

*Intrusion Detection*[^2] is an early term 

Improving threat detection by developing *SIEM use-cases* was popularized by Anton Chuvakin and 

# What does Detection Engineering Do?

# Who does Detection Engineering Serve?

# Why Detection Engineering?

Why do we need an agile, use-case driven, continuous process of detection development and operation?


Because detecting threats is hard. David Bianco's [Pyramid of Pain](https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html)[^4] is a concise model demonstrating that the easiest things to detect are also the easiest for an attacker to change. The most valuable type of indicator is the hardest to detect.

Detection Engineering does simply produce rules that generate alerts. *Detection Analytics* process information to assist with the detection of cyberthreats. 

These analytics can take many forms including rules, alerts, pre-defined searches, reports, dashboards, or *enrichments* to other information. Roth (2022) argues that "detection engineering is by no means limited to the detection of events (activity). It also includes detecting conditions (states), often used in digital forensics or incident response."[^5] For example, detection engineering may develop and inventory of group membership to enrich detection of user activity: when you get an alert about a user, the detection is enriched with contextual information needed to determine if the threat was a false positive or the potential impact of the threat.

Over time emphasis has shifted from the collection of indicators and the automated production of detection signatures, to analysis of attack *Kill Chains* and the techniques used to execute them. From that analysis, the development of data sources and analytics that can reliably detect those techniques. Finally, the data sources and analytics must be implemented and maintained.

Today, the detection of threats, involves a great deal of change: changing threats, changing indicators, changing data sources, and changing detection systems. An agile and continuous process for development and operating detection systems is required. 

That is why we need the modern concept of *Detection Engineering*: Nothing less will suffice.

# 

# Development and Operations


Development of a detection analytics is challenging. 

# Prioritizing Threat Detection Development: Relevance and Feasibility

Don Murdoch emphasized the need to distguish between the *need* for a detection use-case and the *features* that define its capabilities [^3]. 


# 


# Appendix: Disclaimer *Engineer* is a forbidden term in Canada

This article does not describe the practices of licensed *Professional Engineers*. *Detection Engineering*, as used in this article, is a de-facto standard term used globally in *Cybersecurity*: Engineers have not defined practices for cyber threat detection.

# Footnotes

[^1]: *This article was written with the assistance of Generative AI. Specifically, Large Language Models. I used BingChat to help summarize concepts, discover new resources, and judge if my own writing was suitably concise. No text authored by AI was included in this article. It was simply used as a reference. I also used a spell-checker, and those employee Machine Learning too.*

[^2]:  Axelsson, S. (2000, March 14). *[Intrusion Detection Systems: A Survey and Taxonomy](https://neuro.bstu.by/ai/To-dom/My_research/Paper-0-again/For-research/D-mining/Anomaly-D/Intrusion-detection/taxonomy.pdf).

[^3]: Murdoch, D. (2018). [SecOps, SIEM, and Security Architecture Use Case Development](https://www.sans.org/cyber-security-summit/archives/file/summit-archive-1533050405.pdf). SANS Cyber Security Summit, 2018.

[^4]: Bianco, D. (2014, January 17). [The Pyramid of Pain](https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html). *Enterprise Detection & Response Blog.*

[^5]: - Roth, F. (2022, September 11). *[About Detection Engineering](https://cyb3rops.medium.com/about-detection-engineering-44d39e0755f0)*. Medium Blog.



# Appendix: BingChat Notes

## What is detection Engineering?

> Detection engineering is a new approach to threat detection that goes beyond writing detection rules. It is a process that applies systems thinking and engineering to more accurately detect threats¹. Detection engineering is about creating a culture, as well as a process of developing, evolving, and tuning detections to defend against current threats². At its core, detection engineering functions within security operations and deals with the design, development, testing, and maintenance of threat detection logic³. Threat detection logic is any rule, query, or tool used to detect activity that is either malicious, unexpected, or increases the risk that malicious activity will occur³.

Source: Conversation with Bing, 2023-05-22(1) What Is Detection Engineering? - Uptycs. https://www.uptycs.com/blog/what-is-detection-engineering Accessed 2023-05-22.
(2) What is Detection Engineering? – CrowdStrike. https://www.crowdstrike.com/cybersecurity-101/observability/detection-engineering/ Accessed 2023-05-22.
(3) Detection Engineering: A Technical Overview | Panther. https://panther.com/cyber-explained/detection-engineering-benefits/ Accessed 2023-05-22.
(4) Detection Engineering: Defending Networks with Purpose. https://www.sans.org/white-papers/40400/ Accessed 2023-05-22.

