---
published: false
layout: post
title:  "Are Threat Hunting and Detection Engineering the Same Thing?"
summary: "I compare several recent and widely referenced definitions and frameworks for Threat Hunting and Detection Engineering. I conclude that they are categorically the same, sharing a core set of processes, but with differences in expected outcomes. I further conclude that large organizations organize team-functions around specialized aspects of these processes."
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

- Threat Hunting as Proactive
- Threat Hunting as input to Detection Engineering
- Threat Hunting and Detection Engineering as Different Teams
- Detection Engineering as "rule" makers


In this section, I summarized a brief survey a number of authorative and commonly held perspectives. Some of these are *historic*: they were influential, are widely referenced, but are no longer maintained and do not represent emerging practices. For examples: SQRRL, MaGMa, and TaHiTi. Others are new and under active development from leading organizations. For examples: Splunk's PEAK and MITRE's TCHAMP. I have also included several perspective from outspoken voices. In this rapidly changing practice area, these voices are just as influential as as the organizations publishing structured frameworks. For examples, Florian Roth, Alex Texiera, . This survey is not intended to be exhaustive: it captures works that are influential on my understanding.

## SQRRL

Sqrrl added much needed structure and process to what was, until 2015, an ad-hoc activity with an "badass" name. They were purachased by Amazon Web Services in 2018 but archived copies of Sqrrl's influential framework can be found at the [Sqrrl Archive](https://www.threathunting.net/sqrrl-archive) at [The ThreatHunting Project](https://www.threathunting.net/).

"We define hunting as the process of proactively and iteratively searching through networks to detect and isolate advanced threats that evade automated, rule- and signature-based security systems.... Hunting is often machine-assisted but is always driven by an analyst; it can never be fully automated. Automated alerting is important, but cannot be the only thing your detection program relies on. In fact, one of the chief goals of hunting should be to improve your automated detection capabilities by prototyping new ways to detect malicious activity and turning those prototypes into production detection capabilities."

A memorable term introduced by Sqrrl was *Advanced Persistent Defense* to contrast with *Advanced Persistent Threat*. It emphasized the need for continuous monitoring and innovative detection methods.

## MaGMa and TaHiTI

van Os, R., Bakker, M., Bouman, R., van Leeuwen, M., van der Kraan, M., de Volksbank, W., & Piers, A. (2017, November 15). *[TaHiTI Threat Hunting Methodology](https://www.betaalvereniging.nl/wp-content/uploads/DEF-TaHiTI-Threat-Hunting-Methodology.pdf)*

van Os, R., Ladan, F., Casteren, T., Toornstra, R., Metsemakers, R., Neieuwenhuize, L., & Grotenhuis, H. (2017, November 15). *[MaGMa Use Case Framework](https://www.betaalvereniging.nl/wp-content/uploads/FI-ISAC-Use-Case-Framework-Full-Documentation.pdf)*. FI-ISAC NL.

A note of interest: one of the primary authors of MaGMa went on to work at Splunk which today offers the Splunk Security Content Library: a tool that can easily replace the MaGMa spreadsheet planning/tracking tool.

## MITRE TTP-Based Hunting


(Daszczyszak, Ellis, Luke, Whitley, 2019)
Daszczyszak, R., Ellis, D., Luke, S., & Whitley, S. (2019, March). *[TTP-Based Hunting](https://www.mitre.org/sites/default/files/2021-11/prs-19-3892-ttp-based-hunting.pdf)*. 

## Splunk PEAK

[The PEAK Threat Hunting Framework](https://www.splunk.com/en_us/blog/security/peak-threat-hunting-framework.html), from the SURGe by Splunk, is a recent an evolving effort to modernize *Threat Hunting*. It is informed by Sqrrl and TaHiTI, but "incorporates the additional experience and lessons... learned in the last several years."

Rather than define what Threat Hunting is, PEAK defines several types of "hunts", each with its own process, activities, and outcomes. 

- Hypothesis-Driven
- Baseline (AKA Exploratory Data Analysis or EDA)
- Model-Assisted Threat Hunts (M-ATH)

In the PEAK framework, a *Hypothesis-Driven* hunt closely matches older definitions like those from Sqrrl and TaHiTI.

Importantly, there is an overlap in PEAK's definition of Baseline and Model-Assisted hunts and emerging concepts for *Detection Engineering*. For example, Alex T.'s [Table Stakes for Detection Engineering]() argues that DE requires DevOps and Statistical methods. So does PEAK: data pipleines, baseline analysis and machine learning.

## Splunk STRT Approach to Detection Engineering

Splunk's STRT is a "team of security experts [that] develops security content in the form of detections, ML models and SOAR playbooks to help teams address time-sensitive threats and understand attack methods." [Splunk Threat Research Team](https://www.splunk.com/en_us/surge/threat-research.html). They produce Splunk's Enterprise Security Content Updates (ESCU): a library of *detection analytics*.

- Study Threats, Create Datasets, Build Detections, Test Detections, Release [Splunk, 2023, Detection Engineering](https://www.splunk.com/en_us/blog/security/security-content-from-the-splunk-threat-research-team.html)
- 

# Detection Analytics

What is a *Detection Analytic*?

> An analytic describes the observable behavior generated for a TTP. It is the method by which a TTP can be identified. Its hypothesis describes the behavior expected, and the instantiation details its platform-specific implementation. -- [MITRE CAR](https://car.mitre.org/resources/glossary/#analytic)

> “An analytic” is a “process”,  “algorithm”, or “technique” which is generally “mathematical” in essence which takes “data” or “information” as an input and outputs “actionable insights”. -- [ModelOp, What is an analytic anyways?](https://www.modelop.com/blog/analyticops-part-1-what-is-an-analytic-anyway/)

> Splunk Security Content takes MITRE CAR as inspiration and defines several types of analytics: TTP, Baseline, Anomaly, Hunting, Correlation, and Investigation. [Detection Analytic Types](https://github.com/splunk/security_content/wiki/Detection-Analytic-Types)

While the general usage in security operation is that "analytic" means "rule", it is clear that current thinking includes more than that including enrichment of data, searches, and re-usable outputs of statistical analysis (baselines). If you examine all of the common outputs of both Threat Hunting and Detection Engineering processes, you will see that they are all outputs of an analytic process that transforms data into something more actionable: data pipelines, data enrichments, data models, are not significantly different from the work needed to build correlation logic or a complex search. Which in turn as the same work needed to produce a report, visualization, or dashboard. I agrue that these are all "analytics" (noun).

# Is Threat Hunting more Proactive than Detection Engineering?

You will find no shortage of articles stating that Threat Hunting is *pro-active* and that other approaches are *reactive*. Despite the word *hunting* and *detecting* evoking a different sense of urgency, both approach are equally pro-active. The confusion comes from comparing the development and operational components of each practice.

Both are pro-active in their development stage, but when a detection analytic is automated it's operation is *reactive*. Note that in modern definitions of Threat Hunting, there is little emphasis on the implementation of automated detection analytics. The latest frameworks recommend that Threat Hunting operations provide input into Detection Engineering development.

In large organizations where Threat Hunting and Detectino Engineering are continuous activites, executed by seperate specialized teams, one might argue that Threat Hunting is pro-active. In such organizations, the Detection Engineering team is likely to take more input from malware analysis and threat intelligence to create detection analytics from past incidents. However, in those organizations, the Threat Hunting team might be actively seeking out indicators of incidents that have not had. This is also a false comparison. Both processes are taking input from *Threat Intelligence* of known past incidents. Threat Hunting only seem pro-active in that the hunters are searching for activity precisely where it has not occured before, but reacting to external events in environments where it has occured.

On argument that does makes sense is that Threat Hunting can form hypothesis based on external events that have not been directly observed. For example, from new techniques published by exploit developers and vulnerability researchers. It is true that, as defined in modern frameworks, Detection Engineering teams are less likely to prioritize these use-cases. Detection Engineering priroitizes based on the *feasibility* of a use-case. Threat Hunting puts more weight on the *relevance* of a use-case. However, both are hypothesis driven development processes. If this line of argument appeals to you, I would not argue: Modern frameworks emphasize the value of Threat Hunting findings helping to determine the feasibility of a detection analytic, and Detection Engineering taking that as input.

Can Detection Engineering form a hypothesis from speculative external events like new published exploits or vulnerability research? It can, it is just unlikely to prioritize development of detections as the goal of DE is in maintainable analytics. In larger organizations, it will certain *seem* like Detection Engineering is being more reactive. Roth (2022) argues that Detection Engineering always starts with *Detection Ideas*: The engineering process transforms them into useful *Detection Rules*. [^]. Like Threat Hunting, Detection Engineering takes ideas from malware reversing, exploit developers, vulnerability researchers, and many other threat sources. 

Detection Engineering is no less proactive than Threat Hunting, it simply puts more weight on feasbility when prioritizing development effort. Threat Hunters are more likely to apply effort to analytics that are less feasible to automate.

If Threat Hunting is more proactive than Detection Engineering, it is because a specific organization or team chooes to take that approach, often with good reason or due to specialization in large teams.

# If they are different, how are they different?

There is a valid perspective that *Threat Hunting* and *Detection Engineering* are different practices, requiring similar skills and methods. Supporting this perspective are descriptions coming from large organizations, SIEM vendors, and MSSPs.

For example, Splunk SURGE and STRT teams published processes make it clear that *Detection Engineering* is much heavier on DevOps processes and requires rigous development and systems and administration. The threat hunters do not have a requirement to continuously deliver a high quality published software product that will be used by thousands of stakeholders. Perhaps their methods need not be as rigorous.

# Footnotes

[^]: Kostas, T. (2023, Feburary 21). [Detection Engineering VS Threat Hunting](https://kostas-ts.medium.com/threat-hunting-series-detection-engineering-vs-threat-hunting-f12f3a72185f). Threat Hunting Series. 

[^]: Cyborg Security. (2023, May 19). [Guarding the Gates: The Intriccasies of Detection Engineering and Threat Hunting](https://www.cyborgsecurity.com/blog/guarding-the-gates-the-intricacies-of-detection-engineering-and-threat-hunting/).

[^]: Wickramasinghe, S. (2023, February 21). [Threat Hunting vs. Threat Detecting: Two Approaches to Finding & Mitigating Threats](https://www.splunk.com/en_us/blog/learn/threat-hunting-vs-threat-detecting.html). Splunk Blogs.

[^]: Zendejas, D. (2023, May 16). [Detection Engineering vs Threat Hunting](https://zendannyy.substack.com/p/detection-engineering-vs-threat-hunting). Danny's Newsletter.

[^]: Teixeira, A. (2023, February 25). [The dotted lines between Threat Hunting and Detection Engineering](https://ateixei.medium.com/the-dotted-lines-between-threat-hunting-and-detection-engineering-94fa0f7f62ce).

[^]: Wickramasinghe, S. (2023, February 21). [Threat Hunting vs. Threat Detecting: Two Approaches to Finding & Mitigating Threats](https://www.splunk.com/en_us/blog/learn/threat-hunting-vs-threat-detecting.html). Splunk Blogs.

[^]: Delgado, M. (2021, September 02). [4 Differences Between Threat Hunting vs. Threat Detection](https://www.watchguard.com/wgrd-news/blog/4-differences-between-threat-hunting-vs-threat-detection). WatchGuard Blog.

[^]: Bianco, D. (2020, November 2). [Tweet](https://twitter.com/DavidJBianco/status/1323039427472609285). Twitter. 
> When I teach threat hunting, I say "The purpose of threat hunting is not to find new incidents. It's to drive improvement in automated detection." Put simply, threat hunting is detection R&D (at least at the higher levels of hunting maturity).... our hunting outputs are not only detections. We update playbooks and other documentation for our detection engineers and (especially) our response teams. Our primary goal is to improve automated detection, but we see IR improvements as important secondary goals.

[^]: Miller, S. (2018, November 23). [Tweet](https://twitter.com/stvemillertime/status/1066153876032761856). Twitter.
> Enter the DETECTRUM™: I don't really care what we say is detection or hunting or <label>. Instead I like to plot ideas, technologies, services, or any set of logic designed to find evil on a graph that illustrates the 1) data volume 2) threat density and 3) time to validate.

[^]: Roth, F. (2022, October 8). [Capturing Detection Ideas to Improve Their Impact](https://cyb3rops.medium.com/capturing-detection-ideas-to-improve-their-impact-311cf4e1c7a8). Blog.
> Threat Hunters are one source of "detection ideas" and that "detection ideas should be transformed into detection rules to apply ‘leverage’ and maximize their value." Other sources include tools, malware blogs, criminals, and more.
