---
published: false
layout: post
title:  "Detection Engineering Notes"
summary: "I want to better understand the industry landscape and emerging practices in Detection Engineering. These are my notes."
authors: [michael]
categories: [ Blog ]
image: assets/images/detection engineering.png
tags: [detection-engineering,threat-detection,SIEM,SOAR,EDR]
---
{{ page.summary }}

![Graphic image of the title of this blog post]({{page.image | relative_url }})

## What is Detection Engineering?

"Detection Engineering 

## How can I learn more about Detection Engineering?

### Reading

#### Articles

#### Blogs

#### Books

### Listening (Podcasts)

### Watching (Videos)

- [Threat Hunting SANS: What is Detection Engineering? Avigayil Mechtinger](https://www.youtube.com/watch?v=ZcXTUKPK6x0)
- 

### Courses

### Events (Conferences)

## What are popular Detection Engineering Standards and Frameworks?

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
    "The Guru of Detection Engineering" - Avigayle Mechtinger
- [Jake Williams]()
- 
- Microsoft
- Crowdstrike
- Splunk

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

