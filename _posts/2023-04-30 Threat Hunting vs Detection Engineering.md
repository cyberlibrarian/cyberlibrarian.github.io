---
published: false
layout: post
title:  "Are Threat Hunting and Detection Engineering the Same Thing?"
summary: "What is the relationship between Threat Hunting and Detection Engineering? Is one part of the other? What attributes do they share? I compare several widely referenced definitions and frameworks for each. Generally, they are the same set of processes with different perspectives based on the size of the teams implementing them."
authors: [michael]
categories: [ Blog ]
tags: [detection-engineering,threat-hunting,documentation,threat-detection,SIEM,SOAR,EDR]
---
{{ page.summary }}

# Summary

*Threat Hunting* and *Detection Engineer* are terms used to describe innovative and evolving practices for the detection of cyber-threats. The latest models for both emphasize the need for continuous development and execution (DevOps) of data sources and searches, the application statistical methods, and driven by a threat intelligence.

Differences beteween these practices are primarily driven by the need to apply these practices to different stakeholder needs. Large MSPs define successful *Threat Hunting* as generating incident response and new demand for detection engineering whose roles is create reliable high-quality automated detections from lessons learned and from more technical forms of intelligence like malware analysis. Smaller organizations where the capability to execute these practices will be concentrated into a small number of people, will not see value in distinguishing between them: they represent the same processes.

- Threat Hunting is proactive, prioritizing efforts based on based on relevance
- Detection Engineering prioritizes development by relevance and feasbility

Fallacies:

- Threat Hunting execution may trigger Incident Response, but Detection Engineering processes do not. In reality, developing a new detection rule involves the same iterative development process and examination of data as TH. Testing a detection analytic may trigger an Incident Response.

## Dimension

- Proactive vs Reactive
-- Both require proactive, threat-informed, development. Operationally, automated analytics *feel* reactive because they generate detections in reaction to events but the analytic was developed proactively.
- Drivers
- Outputs
-- Both produce *detection analytics*, however operationally these two differ. Modern frameworks agree that Threat Hunting does not provide finished automation or implement automation. They stop there. Detection Engineer has an explicit goal of automating analytics when feasible. In DevOps terms, one output of Threat Hunting processes is adding detection use-cases to Detection Engineering's backlog. Not all analytics developed for Threat Hunting with be feasible for automation. Both produce as output analytics that are NOT alerts: development datasources/data piplelines, developing data enrichments, developing reports, searches, and visualizations of data. They both may develop data models or normalize data to existing data models. These are all "analytics".
- Outcomes
-- Both create detection analytics that can trigger *Incident Response*. However, both create *analytic enrichment* that lead to better investigative outcomes. For example, both curate data sources, both development data enrichments, both before baseline analysis, and both apply statistical methods.
- Development Methods
-- Both require agile development methods. Both are aligned with DevOps practices: there is a continuous process of development of analytics and operations of the systems the analytics are deployed to.
- Who does what?
-- In larger organizations, labour is divided into specialities. Teams may be formed to meet specific stakeholder needs. For example, a large EDR vendor or MSSP may have a team dedicated to "threat hunting" looking just for the latest threats. While another "Detection Engineering" team maybe focused on constantly deploying new malware detection. A SIEM vendor might not have a team that reviews customer data for possible incidents but may have a large team dedicated to creating new analytics to add to a library consumed by it's customers.


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

# Detection Analytics

What is a *Detection Analytic*?

> An analytic describes the observable behavior generated for a TTP. It is the method by which a TTP can be identified. Its hypothesis describes the behavior expected, and the instantiation details its platform-specific implementation. -- [MITRE CAR](https://car.mitre.org/resources/glossary/#analytic)

> “An analytic” is a “process”,  “algorithm”, or “technique” which is generally “mathematical” in essence which takes “data” or “information” as an input and outputs “actionable insights”. -- [ModelOp, What is an analytic anyways?](https://www.modelop.com/blog/analyticops-part-1-what-is-an-analytic-anyway/)

> Splunk Security Content takes MITRE CAR as inspiration and defines several types of analytics: TTP, Baseline, Anomaly, Hunting, Correlation, and Investigation. [Detection Analytic Types](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types)

While the general usage in security operation is that "analytic" means "rule", it is clear that current thinking includes more than that including enrichment of data, searches, and re-usable outputs of statistical analysis (baselines). If you examine all of the common outputs of both Threat Hunting and Detection Engineering processes, you will see that they are all outputs of an analytic process that transforms data into something more actionable: data pipelines, data enrichments, data models, are not significantly different from the work needed to build correlation logic or a complex search. Which in turn as the same work needed to produce a report, visualization, or dashboard. I agrue that these are all "analytics" (noun).

