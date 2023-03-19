---
published: true
layout: post
title:  "Documentation for Detection Engineering"
summary: "Did you know that the MITRE book [11 Strategies of a World-Class Cybersecurity Operations Center](https://www.mitre.org/news-insights/publication/11-strategies-world-class-cybersecurity-operations-center) has appendices outlining the documentation framework need for Security Operations. This includes Detection Engineering!"
authors: [michael]
categories: [ Blog ]
tags: [detection-engineering,threat-detection,SIEM,SOAR,EDR]
---
{{ page.summary }}

Last year, [Deryck Bodnarchuk](https://www.linkedin.com/in/deryck-bodnarchuk/) and I made a pact to improve the documentation of our threat detection systems. This would include documenting an inventory of detection systems, how to access them, how they are configured, a maintenance schedule to keep them updated, procedures for that maintenance, detection rule logic and content, datasource documentation, and helpful search guides for help incident handlers use the systems better. Deryck worked on the systems side, I worked on the "detection content and datasource" side.

Deryck did a much better job than I did! His documentation was well structured and organized. Mine less so: I generated a lot of documents, but only a few stuck with a consistent layout, naming convention, or organization.

I was lacking a framework, and I knew that one must exist. Today, I found it (or close to it)! 

I was re-reading the 2nd Edition of [11 Strategies of a World-Class Cybersecurity Operations Center](https://www.mitre.org/news-insights/publication/11-strategies-world-class-cybersecurity-operations-center) looking for Detection Engineering practices. *Then it hit me*... I had been overlooking the appendices.

On Page 404, Appendix C.3, there is a table of documentation for "Engineering and System Administration". I was reaffirming to see it matches very closely to what Deryck and I came up with on our own. I was delighted to see that it also fills in some of the gaps I was missing!

They don't call this a "documentation framework" but they should. It only lacks some core processes needed to continuously created and maintain the documentation and a metadata taxonomy to make it a complete framework. 

This key document types for SOC Engineering are:

- Monitoring Architecture
- Internal Change Management Processes
- Systems and Sensors Maintenance and Build Instructions
- Operational, Functional, and Systems Requirements
- Budget and current spending (capital and operational expenditures)
- Unfunded Requirements
- Sensor and SIEM Detections/Analytics/Content Lists(s)
- SOC System Inventory
- Network Diagrams

Deryck, I think you read this, your mind will be blown. As always, you knew the "best practices" before I can find the standard proving it.

## [Detection Engineering Notes]({% link _pages/detection-engineering-notes.md %})

I have put additional details in my [Detection Engineering Notes]({% link _pages/detection-engineering-notes.md %}) page, along with commentary and my own experiences/practices. I'm working on a framework of DE tasks that would align with documented artifacts. 

