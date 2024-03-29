---
layout: page
permalink: "/detection-engineering-notes"
title:  "Detection Engineering Notes"
summary: "I want to better understand the industry landscape and emerging practices in Detection Engineering and Threat Hunting. These are my notes on DE perspectives, frameworks, processes, tools, and people to learn from."
authors: [michael]
categories: [ Blog ]
tags: [detection-engineering,threat-detection,SIEM,SOAR,EDR]
---
Last Update: 2023-05-13

{{ page.summary }}

## What is Detection Engineering?

*Detection Engineering* is the populized term to describe the practice of designing, developing, and maintaining systems for the detection of cyber threats. It is closely related to *Threat Hunting* and shares frameworks and processes. It is a not a discipline of Engineering as defined by many regulatory bodies, but a term populized through wide-accepted usage in cybersecurity. It is used to distinguish between the roles of *Threat Intelligence* and *Incident Response* in *Security Operations*. The specific definition varies, but the term itself is now widely used.

My working definition (subject to change):

> Modern *Detection Engineering* and *Threat Hunting* are agile threat-informed defense practices that develop and operationalize threat *detection analytics*. These practices require threat analysis, data engineering, design and management of detection systems, development of detection analytics, and operation/execution of threat detection. They are DevOps practices driven by threat intelligence, enabled by data modeling on large datasets, and increasingly requiring the application of statistical techniques. The product of these practices are *analytics*: rules, signatures, dashboards, reports, searches, data models, visualizations, and/or "enrichments". They are both functions of *Security Operations* and distinct from *Incident Response*, *Vulnerability Management*, and *Threat Intelligence*.

## Some perspectives on how to define Detection Engineering/Threat Hunting:

> Threat hunting and detection engineering are different specializations, but are closely related. They have common goal of finding attackers using available data, whether its the attackers that got past your detections (threat hunting) or the next ones through (detections). -- Mark Simos

> Detection engineering is the process of identifying threats before they can do significant damage. Detection engineering is about creating a culture, as well as a process of developing, evolving, and tuning detections to defend against current threats. -- CrowdStrike

> Detection engineering transforms information about threats into detections.... Detection engineering transforms an idea of how to detect a specific condition or activity into a concrete description of how to detect it. -- Florian Roth

> Enter Threat hunting - the proactive practice of ferreting out those sneaky cyber-rodents. Or, if you insist on a more formal definition, “any manual or machine-assisted process intended to find security incidents missed by an organization’s automated detection systems.” Either way, hunting is a great way to drive improvement in automated detection and help you stay ahead of the attackers. -- David Bianco

> When I teach threat hunting, I say "The purpose of threat hunting is not to find new incidents. It's to drive improvement in automated detection." Put simply, threat hunting is detection R&D (at least at the higher levels of hunting maturity).... our hunting outputs are not only detections. We update playbooks and other documentation for our detection engineers and (especially) our response teams. Our primary goal is to improve automated detection, but we see IR improvements as important secondary goals. -- [David Bianco](https://twitter.com/DavidJBianco/status/1323253575150194688)

> Detection engineering is by no means limited to the detection of events (activity). It also includes detecting conditions (states), often used in digital forensics or incident response. -- Florian Roth

> A Threat Detection Engineer is someone who applies domain knowledge on designing, building or maintaining detection content in the form of detections generating alerts; or interfaces in the form of dashboards or reports supporting the security monitoring practice within an organization. -- Alex Teixeira

> Detection engineering is a process—applying systems thinking and engineering to more accurately detect threats. The goal is to create an automated system of threat detection which is customizable, flexible, repeatable, and produces high quality alerts for security teams to act upon. -- Laura Kenner, uptycs

> Detection engineering functions within security operations and deals with the design, development, testing, and maintenance of threat detection logic. -- Mark Stone, panther

> Detection engineers design and build security systems that constantly evolve to defend against current threats. -- Josh Day, gigamon

> Threat hunting is an active means of cyber defense in contrast to traditional protection measures, such as firewalls, intrusion detection and prevention systems, quarantining malicious code in sandboxes, and Security Information and Event Management technologies and systems. Cyber threat hunting involves proactively searching organizational systems, networks, and infrastructure for advanced threats. The objective is to track and disrupt cyber adversaries as early as possible in the attack sequence and to measurably improve the speed and accuracy of organizational responses. Indications of compromise include unusual network traffic, unusual file changes, and the presence of malicious code. Threat hunting teams leverage existing threat intelligence and may create new threat intelligence, which is shared with peer organizations, Information Sharing and Analysis Organizations (ISAO), Information Sharing and Analysis Centers (ISAC), and relevant government departments and agencies. -- NIST SP 800-53 v5: RA-10

> Detection Engineering sits at the intersection of InfoSec, Cloud Infrastructure, DevOps, and Software Development.  -- [Jack Naglieri](https://jacknaglieri.substack.com/p/detection-engineer-pt-1)

> If you want to scale your detection program, you need to hire a Detection Engineering team that can complement each other in the following areas: 1. Subject matter expertise in security, 2. Software engineering, 3. Statistics -- [Zack Allen](https://www.detectionengineering.net/p/table-stakes-for-detection-engineering)

> Detection engineering is a new approach to threat detection. More than just writing detection rules, detection engineering is a process — applying systems thinking and engineering to more accurately detect threats. Detection Engineering involves the research, design, development, testing, documentation, deployment and maintenance of detections/analytics and metrics. - [Sohan G](https://d4rkciph3r.medium.com/establishing-a-detection-engineering-program-from-the-ground-up-b170811166c)

> Detection Engineering is a capability that researches and models threats in order to deliver modern and effective threat detections. What is Detection Engineering? Goal is to provide automated analytical capabilities {hunts} that can capture and detect the behaviours and TTPs of adversaries. -- [Atanas Viyachki, Senior Threat Hunter@Weatlthsimple](https://defcontoronto.com/wp-content/uploads/2023/03/DetectionEngineeringFramework-AtanasViyachki.pdf)

> Detection engineering is the continuous process of deploying, tuning, and operating automated infrastructure for finding active threats in systems and orchestrating responses. Indeed, both the terms “detection” and “engineering” carry important connotations when it comes to the new approaches to security we’re discussing. -- [Jamie Lewis](https://medium.com/swlh/detection-engineering-for-cloud-native-security-190afdd4558c)

### Are Threat Hunting and Detection Engineering the Same Thing?

A number of emerging frameworks and defitions for *Threat Hunting* overlap with *Detection Engineering*. For this reason, I will include Threat Hunting models, methods, and frameworks. The newest thinking provides fewer differences, mostly around goals and who-does-what. 

There appear to be more similarities that differences in processes, with differences proposed depending on the size of the organization. For example, large MSPs see a greater distinction than a mid-size financial institution would: the MSP has entire departments who much detect threats, and labour must be divided. A single organiztaion with an Information Security department of 20 people might want a one or two people to take on all detection development tasks.

- Cyborg Security. (2023, May 19). [Guarding the Gates: The Intriccasies of Detection Engineering and Threat Hunting](https://www.cyborgsecurity.com/blog/guarding-the-gates-the-intricacies-of-detection-engineering-and-threat-hunting/).
- Zendejas, D. (2023, May 16). [Detection Engineering vs Threat Hunting](https://zendannyy.substack.com/p/detection-engineering-vs-threat-hunting). Danny's Newsletter.
- Teixeira, A. (2023, February 25). [The dotted lines between Threat Hunting and Detection Engineering](https://ateixei.medium.com/the-dotted-lines-between-threat-hunting-and-detection-engineering-94fa0f7f62ce).
- Kostas, T. (2023, Feburary 21). [Detection Engineering VS Threat Hunting](https://kostas-ts.medium.com/threat-hunting-series-detection-engineering-vs-threat-hunting-f12f3a72185f). Threat Hunting Series. 
- Wickramasinghe, S. (2023, February 21). [Threat Hunting vs. Threat Detecting: Two Approaches to Finding & Mitigating Threats](https://www.splunk.com/en_us/blog/learn/threat-hunting-vs-threat-detecting.html). Splunk Blogs.
- Delgado, M. (2021, September 02). [4 Differences Between Threat Hunting vs. Threat Detection](https://www.watchguard.com/wgrd-news/blog/4-differences-between-threat-hunting-vs-threat-detection). WatchGuard Blog.

### Perspectives

- Florian Roth : [About Detection Engineering](https://cyb3rops.medium.com/about-detection-engineering-44d39e0755f0)
- Alex Teixeira : [What does it mean to be a threat detection engineer?](https://ateixei.medium.com/what-does-it-mean-to-be-a-threat-detection-engineer-f14bf5916aac)
- Mark Simos : [Typical SecOps Role Evolution](https://www.linkedin.com/posts/marksimos_ive-been-thinking-deeply-about-the-evolution-activity-7030370158208544768-HkaJ/?originalSubdomain=hk)
- Dave Bianco : 
- CrowdStrike : [What is Detection Engineering?](https://www.crowdstrike.com/cybersecurity-101/observability/detection-engineering/#:~:text=Detection%20engineering%20is%20the%20process,to%20defend%20against%20current%20threats.)
- GitHub : [Awesome Detection Engineering](https://github.com/infosecB/awesome-detection-engineering)
- Uptycs : [What Is Detection Engineering?](https://www.uptycs.com/blog/what-is-detection-engineering)
- Panther : [A Technical Primer in Detection Engineering](https://panther.com/cyber-explained/detection-engineering-benefits/)
- Gigamon : [So, You Want to Be a Detection Engineer?](https://blog.gigamon.com/2020/02/24/so-you-want-to-be-a-detection-engineer/)
- Red Canary : [Behind the Scenes with Red Canary's Detection Engineering Team](https://redcanary.com/blog/detection-engineering/)
- Secureworks : [Threat Hunting as an Official Cybersecurity Discipline](https://www.secureworks.com/blog/threat-hunting-as-an-official-cybersecurity-discipline)
- NIST SP800-53 v5 : [RA-10: Threat Hunting](https://csf.tools/reference/nist-sp-800-53/r5/ra/ra-10/)
- Jack Naglieri : [Think Like a Detection Engineer](https://jacknaglieri.substack.com/p/detection-engineer-pt-1)
- Zack Allen : [Table Stakes for Detection Engineering](https://www.detectionengineering.net/p/table-stakes-for-detection-engineering)

## Can I get certified as a Detection Engineer?

- [ATT&CK Threat Hunting Detection Engineering Certification Path](https://mad-certified.mitre-engenuity.org/collection/9edbe772-c054-4004-bf4c-f5e7b09d2640)
-- Training is part of [MITRE MAD](https://mitre-engenuity.org/cybersecurity/mad/mad-curriculum/) which is USD$500/year.
- [GIAC Certified Detection Analyst (GCDA)](https://www.giac.org/certifications/certified-detection-analyst-gcda/)

## How can I learn more about Detection Engineering?

## Maturity Models

- [The DML Model](https://ryanstillions.blogspot.com/2014/04/the-dml-model_21.html), Ryan Stillions
- [Detection Engineering Maturity Matrix](https://detectionengineering.io/), Kyle Bailey
    - [Detectin Engineering Maturity Matrix](https://kyle-bailey.medium.com/detection-engineering-maturity-matrix-f4f3181a5cc7), Blog post by Kyle Bailey.
- [The Hunting Maturity Model (HMM)](https://www.threathunting.net/files/The%20Threat%20Hunting%20Reference%20Model%20Part%201_%20Measuring%20Hunting%20Maturity%20_%20Sqrrl.pdf), Sqrrl Threat Hunting Reference Model (*no longer maintained*)

### Reading

#### Articles


- Roth, F. (2022, September 11). *[About Detection Engineering](https://cyb3rops.medium.com/about-detection-engineering-44d39e0755f0)*. Medium Blog.
- [The dotted lines between Threat Hunting and Detection Engineering](https://ateixei.medium.com/the-dotted-lines-between-threat-hunting-and-detection-engineering-94fa0f7f62ce)
- [Prioritization of the Detection Engineering Backlog](https://posts.specterops.io/prioritization-of-the-detection-engineering-backlog-dcb18a896981)
- [Detection Engineering with MITRE Top Techniques & Atomic Red Team](https://fourcore.io/blogs/detection-engineering-with-mitre-engenuity-atomic-red-team)
- [How to Improve Security Monitoring with Detection Engineering Program](https://blogs.oracle.com/cloudsecurity/post/how-to-improve-security-monitoring-with-detection-engineering-program)
- [The Evolution of Security Operations and Strategies for Building an Effective SOC](https://www.isaca.org/resources/isaca-journal/issues/2021/volume-5/the-evolution-of-security-operations-and-strategies-for-building-an-effective-soc) (ISACA, Lakshmi Narayanan Kaliyaperumal)
- Kenner, L. (2022, July 14). [What is Detection Engineering](https://www.uptycs.com/blog/what-is-detection-engineering). Uptycs Blog.
- [Threat-Informed Defense Ecosystem](https://start.me/p/X25q7l/threat-informed-defense-ecosystem) by Micah V.
- Bastidas, L. (2023, April 11). *[On the road to detection engineering](https://www.trustedsec.com/blog/on-the-road-to-detection-engineering/)*. TrustedSec Blog.

#### Blogs

- [Detection Engineering Weekly from Zack Allen](https://www.detectionengineering.net/)
- [Blog Posts Tagged "Detection Engineering" on Medium](https://medium.com/tag/detection-engineering)
- [Florian Roth](https://cyb3rops.medium.com/)
- [Alex Teixeira: When Data speaks, are you ready to listen?](https://ateixei.medium.com/)
- [MITRE ATT&CK Blog](https://medium.com/mitre-attack)
- [Anton Chuvakin](https://medium.com/@anton.chuvakin)

#### Books

- [11 Strategies of a World-Class Cybersecurity Operations Center](https://www.mitre.org/news-insights/publication/11-strategies-world-class-cybersecurity-operations-center)
- [Malware Analysis and Detection Engineering](https://www.google.ca/books/edition/Malware_Analysis_and_Detection_Engineeri/TDGWzQEACAAJ?hl=en)
- [Agile Security Operations](https://www.kobo.com/ca/en/ebook/agile-security-operations)

### Listening (Podcasts)

- [The Mysteries of Detection Engineering: Revealed!](https://cloud.withgoogle.com/cloudsecurity/podcast/the-mysteries-of-detection-engineering-revealed/)

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

#### Frameworks for Detection Engineering/Threat Hunting
- [MITRE TTP-Based Hunting (TCHAMP)](https://www.mitre.org/sites/default/files/2021-11/prs-19-3892-ttp-based-hunting.pdf)
- [Splunk SURGE PEAK](https://www.splunk.com/en_us/blog/security/peak-threat-hunting-framework.html)
- [Open Detection Engineering Framework](https://github.com/wealthsimple/odef)
- [MaGMa: a framework and tool for use case management](https://www.betaalvereniging.nl/en/safety/magma/)
-- The MaGMa Use Case Framework (UCF) is a framework and tool for use case management and administration on security monitoring. MaGMa's tool is decprecated and not maintained but the methodology remains sound well aligned with current practices. It is documented where other practices are often shared word-of-mouth. The primary author works at Splunk which now offers the Entprise Security Content library, with MaGMa like features.
- [TaHiTI: Threat Hunting Methodology](https://www.betaalvereniging.nl/en/safety/tahiti/)
-- Aligned with MaGMa, the TaHiTI methodology for threat hunting is created with real hunting practice in mind and provides organization with a standardized and repeatable approach to their hunting investigations. The methodology uses 3 phases and 6 steps and integrates threat intelligence throughout its execution.

#### Standards for Implementing Detection Engineering Processes
- [MITRE ATT&ACK](https://attack.mitre.org/)
- [MITRE DETT&CT](https://github.com/rabobank-cdc/DeTTECT)
- [The Cyber Kill Chain](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html)
-- There are many variants of the killchain model. Lockheed Martin's is often cited. 
- [The Pyramid of Pain](https://detect-respond.blogspot.com/2013/03/the-pyramid-of-pain.html)
- [Detection Engineering Maturity Matrix](https://detectionengineering.io/)
-- See also Kyle Bailey's post [Detection Engineering Maturity Matrix](https://kyle-bailey.medium.com/detection-engineering-maturity-matrix-f4f3181a5cc7)
- [The DML Model](https://ryanstillions.blogspot.com/2014/04/the-dml-model_21.html)
- [Purple Team Exercise Framework (PTEF)](https://scythe.io/ptef)
-- This is compatible with and includes a role for Detection Engineering

### Naming Conventions
- From LASCON talk by 
-- Primary Key:SCOPE:TTP:Short name
-- Scope is servers, workstations, or something more granular

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
- [MITRE ATT&CK datasource mapping](https://github.com/mitre-attack/attack-datasources)
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

### Malware Analysis

- VirusTotal
- Any.run
- Hybrid Analysis
- Cisco Malware Analytics
- IDA Pro

## Who are the leaders in Detection Engineering?

These are leaders in the sense, that they are people I follow! I have quite a few more to add to this list, many quoted earlier this these notes.

- [Florian Roth](https://twitter.com/cyb3rops)
- [David J Bianco](https://detect-respond.blogspot.com/)
- [Roman Daszczyszak](https://twitter.com/rdunspellable?lang=en)
- [Alex Teixeira](https://ateixei.medium.com/)
- [Kyle Bailey](https://kyle-bailey.medium.com/)
- TBD.. what about the folks at MITRE who designed MITRE TTP-Based Hunting etc?
- Rob van Os. Primary author of MaGMa, TaHiTI, and SOC-CMM.

## Where does Detection Engineering fit into the NIST Cybersecurity Framework

That's complicated. The NIST CSF has an entire category called *Detect* but various activities that are part of *Detection Engineering* and *Threat Hunting* are found in other CSF categories as well.

It can be modeled as a control to address the *Identity* category. For example, through NIST 800-53v5 RA-10: Threat Hunting. Have they confused the role that *Threat Intelligence* has in informing *Threat Hunting*? No. The control definition clearly outlines a requirement to establish a capability to monitor for and detect threats. Multiple controls, including threat hunting must be applied toward this requirement.

## What is the relationship between Detection Engineering and Incident Response?

Incident Response is the key stakeholder in the development of detection analytics. In the past, or in small organizations, they may also be the developer of detection analytics.

The creation of detection rules and their "tuning" to eliminate false-positives has often been described as an activity carried about by incident responders. For example, a corporate security team, the incident response manage and use the SIEM for detection. The rules exist for them, and they create those rule in response to past incidents or from a library of pre-defined rules that they customize for their environment.

This approach may be considered "historic" and is not emphasized in modern frameworks. It is not that incident responder cannot or should not be involved, it is that their role is operational and should be the consumer of good analytics, the driver of the development of new analytics, and not the developers of analytics. They are a stakeholder, perhaps the most important stakeholder!

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

In some larger organizations, especially security product vendors and MSP, a core activitity is analyzing new malware samples to extract useful indicators and to turn those into detection rules. The continuous deployment of new detection signatures is driven by malware analysis, and malware analysis might be considered a core skill required of those in a Detection Engineering role. Given that malware hashes are trivially changed, this activity involves more in-depth understanding of malware behaviour and the identification of invariant observables as well as behavior-based detections.

