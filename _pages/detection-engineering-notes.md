---
layout: page
permalink: "/detection-engineering-notes"
title:  "Detection Engineering Notes"
summary: "I want to better understand the industry landscape and emerging practices in Detection Engineering. These are my notes on DE perspectives, frameworks, processes, tools, and people to learn from."
authors: [michael]
categories: [ Blog ]
tags: [detection-engineering,threat-detection,SIEM,SOAR,EDR]
---
Last Update: 2023-03-19

{{ page.summary }}

## What is Detection Engineering?

> Detection engineering is the process of identifying threats before they can do significant damage. Detection engineering is about creating a culture, as well as a process of developing, evolving, and tuning detections to defend against current threats. -- CrowdStrike

### Perspectives

- Florian Roth : [About Detection Engineering](https://cyb3rops.medium.com/about-detection-engineering-44d39e0755f0)
- CrowdStrike : [What is Detection Engineering?](https://www.crowdstrike.com/cybersecurity-101/observability/detection-engineering/#:~:text=Detection%20engineering%20is%20the%20process,to%20defend%20against%20current%20threats.)
- GitHub : [Awesome Detection Engineering](https://github.com/infosecB/awesome-detection-engineering)
- Uptycs : [What Is Detection Engineering?](https://www.uptycs.com/blog/what-is-detection-engineering)
- Panther : [A Technical Primer in Detection Engineering](https://panther.com/cyber-explained/detection-engineering-benefits/)
- Gigamon : [So, You Want to Be a Detection Engineer?](https://blog.gigamon.com/2020/02/24/so-you-want-to-be-a-detection-engineer/)
- Red Canary : [Behind the Scenes with Red Canary's Detection Engineering Team](https://redcanary.com/blog/detection-engineering/)
- Alex Teixeira : [What does it mean to be a threat detection engineer?](https://ateixei.medium.com/what-does-it-mean-to-be-a-threat-detection-engineer-f14bf5916aac)
- Mark Simos : [Typical SecOps Role Evolution](https://www.linkedin.com/posts/marksimos_ive-been-thinking-deeply-about-the-evolution-activity-7030370158208544768-HkaJ/?originalSubdomain=hk)

## Can I get certified as a Detection Engineer?
Maybe. I never thought about that before.

- [ATT&CK Threat Hunting Detection Engineering Certification Path](https://mad-certified.mitre-engenuity.org/collection/9edbe772-c054-4004-bf4c-f5e7b09d2640)
-- Training is part of [MITRE MAD](https://mitre-engenuity.org/cybersecurity/mad/mad-curriculum/) which is USD$500/year.
- [GIAC Certified Detection Analyst (GCDA)](https://www.giac.org/certifications/certified-detection-analyst-gcda/)

## How can I learn more about Detection Engineering?

### Reading

#### Articles

- [The dotted lines between Threat Hunting and Detection Engineering](https://ateixei.medium.com/the-dotted-lines-between-threat-hunting-and-detection-engineering-94fa0f7f62ce)
- [Prioritization of the Detection Engineering Backlog](https://posts.specterops.io/prioritization-of-the-detection-engineering-backlog-dcb18a896981)
- [Detection Engineering with MITRE Top Techniques & Atomic Red Team](https://fourcore.io/blogs/detection-engineering-with-mitre-engenuity-atomic-red-team)
- [How to Improve Security Monitoring with Detection Engineering Program](https://blogs.oracle.com/cloudsecurity/post/how-to-improve-security-monitoring-with-detection-engineering-program)

#### Blogs

- [Blog Posts Tagged "Detection Engineering" on Medium](https://medium.com/tag/detection-engineering)
- [Florian Roth](https://cyb3rops.medium.com/)
- [Alex Teixeira: When Data speaks, are you ready to listen?](https://ateixei.medium.com/)
- [MITRE ATT&CK Blog](https://medium.com/mitre-attack)
- 


#### Books

- [11 Strategies of a World-Class Cybersecurity Operations Center](https://www.mitre.org/news-insights/publication/11-strategies-world-class-cybersecurity-operations-center)
- [Malware Analysis and Detection Engineering](https://www.google.ca/books/edition/Malware_Analysis_and_Detection_Engineeri/TDGWzQEACAAJ?hl=en)
- [Agile Security Operations](https://www.kobo.com/ca/en/ebook/agile-security-operations)

### Listening (Podcasts)

### Watching (Videos)

- [Detection Engineering Methodologies](https://www.youtube.com/watch?v=qy_0wGMJc9w)
- [Threat Hunting SANS: What is Detection Engineering? Avigayil Mechtinger](https://www.youtube.com/watch?v=ZcXTUKPK6x0)
- [Resilient Detection Engineering](https://www.youtube.com/watch?v=zMPouyUNX5c)
- [Detection as Code: Detection Development Using CI/CD](https://www.youtube.com/watch?v=_JEvyem4ryg)
- [Threat-Informed Detection Engineering](https://www.youtube.com/watch?v=2czm8dhziX8)
- [Leveling Up Your Detection Engineering](https://www.youtube.com/watch?v=47Jd7oByorI)
- [Measuring Detection Engineering Teams](https://www.youtube.com/watch?v=Dxccs8UDu6w)
- [Security Onion Essentials - Detection Engineering](https://www.youtube.com/watch?v=IS2SOlDedPc)

### Courses

### Events (Conferences)

## What are the core Detection Engineering Processes?

TODO. See articles above for now.

## What tasks should a Detection Engineering Program document?

Appendix C.3 of the MITRE book [11 Strategies of a World-Class Cybersecurity Operations Center](https://www.mitre.org/news-insights/publication/11-strategies-world-class-cybersecurity-operations-center) outlines a framework for Detection Engineering/SOC Systems Administrator documentation. In a past job, I worked together with a SOC Syadmin, collaborated on documentation that was similar. I was delighted when I read this appendix and found it was a strong match for what we did. It drove new effeciencies, supported better understanding by incident handlers, and ensured our systems were well maintained and worked.

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

I like to focus more on the documentation of use-case development. In the MITRE book that would be "Sensor and SIEM Detections/Analytics/Content List(s)" as well as "Internal Change Management Processes" primarily. Below is my own framework for the medium-grained tasks a Detectin Engineer would carry out. You can think of each item below as being an artifact or task documented in Jira or Confluence etc.

- Document use-case
-- Taking as input some need, define the use-case so that it maybe reviewed and prioritized and added to the backlog
- Develop use-case
-- Input is a documented need for the use-case. Perform in-depth requirements analysis, data wrangling, iterative development of detection and data sources, and full documentation. Output is a test detection in non-production ready to be reviewed for acceptance by stakeholders, and for final implementation.
- Implement use-case
-- Input is an developed use-case that has passed acceptance. Implement it in production and remove it from the backlog.
- Monitor use-cases
-- Input is all production use-cases. Monitor use-cases and periodically review them for relevancy and effectivness. Output is requests to retire, enhance, or maintain the use-cases
- Retire use-case
-- Input is a request from monitoring of all use-cases. Ensure the use-case is disabled tracking anything that has dependencies on the use-case. If necassary create a new use-case to replace this one if others depend on it but it needs to be retired. Output is confirmation that retirement has not caused adverse impact.
- Plan threat-hunt
-- Input is demand for a new use-case. Generate a hypothesis and test plan. Describe data sources needed, effort and resources required and a schedule. Output is a plan and schedule ready for approval.
- Execute threat-hunt
-- Input is a threat hunt plan that has been approved. Gather the required team, and on schedule execute the hunt. Output is documented findings, and possibly escalation to incident response.
- Develop metric
-- Input is a deman from a stakeholder or a documented use-case ready for development. Develop a way to measure the effectiveness of a use-case, or some aspect of the DE program. Output is the logic/process for a scheduled report dashboard or some data.
- Implement metric
-- Input is a developed metric. Implement it and remove it from the backlog.
- Report metrics
-- Input is all developed, implemented metrics. Operationize reporting. Output is feedback into the use-case development process or advise to stakeholders outside DE.
- Document datasource
- Implement datasource
- Monitor datasource
- 

## What are popular Detection Engineering Standards and Frameworks?

### Frameworks
- [Open Detection Engineering Framework](https://github.com/wealthsimple/odef)
- [MITRE ATT&ACK](https://attack.mitre.org/)
- [The Cyber Kill Chain](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html)
-- There are many variants of the killchain model. Lockheed Martin's is often cited. 
- [The Pyramid of Pain](https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html)
- [Detection Engineering Maturity Matrix](https://detectionengineering.io/)
-- See also Kyle Bailey's post [Detection Engineering Maturity Matrix](https://kyle-bailey.medium.com/detection-engineering-maturity-matrix-f4f3181a5cc7)
- [The DML Model](https://ryanstillions.blogspot.com/2014/04/the-dml-model_21.html)
- [Purple Team Exercise Framework (PTEF)](https://scythe.io/ptef)
-- This is compatible with and includes a role for Detection Engineering
- [MaGMa: a framework and tool for use case management](https://www.betaalvereniging.nl/en/safety/magma/)
-- The MaGMa Use Case Framework (UCF) is a framework and tool for use case management and administration on security monitoring. MaGMa's tool is decprecated and not maintained but the methodology remains sound well aligned with current practices. It is documented where other practices are often shared word-of-mouth. The primary author works at Splunk which now offers the Entprise Security Content library, with MaGMa like features.
- [TaHiTI: Threat Hunting Methodology](https://www.betaalvereniging.nl/en/safety/tahiti/)
-- Aligned with MaGMa, the TaHiTI methodology for threat hunting is created with real hunting practice in mind and provides organization with a standardized and repeatable approach to their hunting investigations. The methodology uses 3 phases and 6 steps and integrates threat intelligence throughout its execution.

### Naming Conventions
- From LASCON talk by 
-- Primary Key:SCOPE:TTP:Short name
-- Scope is servers, workstations, or something more granular
-- 

### Detection Specification Languages/Formats
- Sigma
- YARA
- Splunk SPL
- Microsoft KQL
- Snort Rules
- GraphQL
- YAML

### Managing a Backlog of Work
- JIRA

### Processes

- Agile Use Case Detection Methodologies
- DevOps CI/CD

### Standards

- Sigma
- 


## What tools are popular for Detection Engineering?

### EDR
- Wazuh
- CrowdStrike
- Microsoft Defender for Endpoint

### SIEM
- Microsoft Sentinel
- Splunk Enterprise Security
- 

### SOAR
- Splunk SOAR
- LogicHub
- Palo Alta Cortex
- CrowdStrike Fusion

### Analytics
- [MITRE Cyber Analytics Repository (CAR)](https://car.mitre.org/)
- Python (Pandas) 
- Jupyter Notebooks
- Splunk Enterprise Security CIM Datamodels
- Microsoft Excel
 
### Data Sources (Event Logs)
- Sysmon
- Linux auditd
- Filebeat
- Windows Events
- syslog
- Firewall Logs
- Zeek (network events)
- DNS logs
- Anti-virus Alerts
- Active Directory changes
- AWS CloudTrail
- 

### Malware Analysis

- VirusTotal
- Any.run
- Hybrid Analysis
- Cisco Malware Analytics
- IDA Pro

## Who are the leaders in Detection Engineering?

- [Florian Roth](https://twitter.com/cyb3rops)
- [David J Bianco](https://detect-respond.blogspot.com/)
- [Alex Teixeira](https://ateixei.medium.com/)
- [Kyle Bailey](https://kyle-bailey.medium.com/)

## What is the relationship between Detection Engineering and Incident Response?

## What is the relationship between Detection Engineering and Threat Hunting?

Threat Hunting and Detection Engineering go hand-in-hand. Threat Hunting methods are used by Detection Engineers to validate their detection logic, data sources, and measure effectiveness. That said, Threat Hunting has additional outcomes unrelated to Detection Engineering goals, and may trigger incident response. 

Most Detection Engineering use-cases begin with a Threat Hunt to validate and priorize the use-case. If the threat hunt proves difficult, it helps estimate the effort of developing the use-case for detecting that threat. If the threat hunt yeilds few false positives, it indicates that the use-case could be highly effective and should get higher priority. If the threat hunt fails due to lack of data, it may indicate that developmen to the use-case should be deferred until the datasource can be developed.

## What is the relationship between Detection Engineering and Threat Intelligence?

The need for new detections is often driven by threat intelligence. We want to detect threats before they become incidents and the earliest needs may come from threat intelligence analysis. For example, if Qakbot has changed their methods but your organization has not yet encountered them, threat intelligence may be able to provide information on how to detect the new methods days before you are attacked.

> A good detection engineer reads threat reports differently than a malware or TI analyst. 
> He/she discovers detection opportunities, pivots and writes rules for any trace the reported threat may have left.
> -- [Florian Roth](https://twitter.com/cyb3rops/status/1405523131976929287)

## What is the relationship between Detection Engineering and Offensive Security?

## What is the relationship between Detection Engineering and IT Asset Inventory?

Detection Engineering both consumes and produces asset inventories. Detection Engineering crucially requires quality inventory of assets, identifies, and configurations. 

If you want to measure the converage of your detections for an specific threat, you will need to have an inventory of assets targeted by, exposed to, or vulnerable to the threat. If you don't have a good inventory, you will not know how effective your detection will be. For example, if you have a detection for exploitation of a vulnerability in MS SQL Server, but you don't know how many SQL Servers you have, or their addresses, you cannot determine if your detection will actually work.

Detection Engineers often have specific inventory requirements that others do not. For example, knowing which security agents are present, knowing how assets are configured, knowing what permissions an identity has. These all can be used to enrich detections to priotize alerts by priority of the asset or severity of the detected threat. Without this additional information, you can detect a threat, but not detemine how urgent a response to that threat is.

## What is the relationship between Detection Engineering and Malware Analysis?

