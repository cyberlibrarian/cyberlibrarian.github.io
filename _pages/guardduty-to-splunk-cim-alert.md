---
layout: page
permalink: "/guardduty-to-splunk-cim-alert"
title:  "Mapping AWS GuardDuty Finding to Splunk CIM Alert Datamodel"
summary: "A method for mapping AWS GuardDuty Findings to Splunk's CIM Alert Datamodel. While the common GuardDuty Finding fields are easy to map to the CIM Alert datamodel, it is hard to map the actor and target of a finding. This method provides a dynamic, easy to maintain, way of performing that mapping."
authors: [michael]
categories: [ Blog ]
last-update: "2023-07-16 16:43 UTC"
tags: [detection-engineering,threat-detection,SIEM,SOAR,Splunk,splunk-enterprise-security,datamodel,aws-guardduty,GuardDuty]
---
Last Update: {{page.last-update}} (Draft)

{{ page.summary }}

## Background

*TODO: write an introduction*

Why not provide this as a Splunk Add-on? I have provided this to support understanding the two different alert formats. Understanding our data is important because it changes but the patterns for performing this type of mapping are less variant. While much of what I have documented is better implemented in Splunk as specific knowledge objects and settings, the purpose of the document is to understand how to normalize a complex detection event to CIM's generic format.

By practicing this kind of analysis and design we can apply this method to other formats from other detection engines in the future.

### AWS GuardDuty Findings

### Splunk CIM Alert Datamodel

## Undertanding the CIM Alert Fields
Our goal is to map [AWS GuarDuty Finding](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_findings-summary.html) fields to [Splunk CIM Alert datamodel](https://docs.splunk.com/Documentation/CIM/5.1.1/User/Alerts) fields. Here is a summary of the 

## Parsing the GuardDuty Finding Format

### Parsing the Finding Overview
The GuardDuty Finding overview contains descriptive metadata to help us understand the type of finding, how it was detected, who the actor was, and was resource was affected. The finding overview data fills in most of the CIM Alert fields.

CIM Alert Field | GuardDuty Finding Field | Description
-------------------------------------------------------
app | "AWS GuardDuty" | What generated the alert?
description | detail.description
dest | TBD | The thing affected by detected activity
dest_type | TBD | The type of thing affected by the activity detected
id | detail.findingId | A unique ID for this specific occurence of the detection type. Updates or related details will share this ID
mitre_technique_id | n/a | We could create a lookup table to perform this mapping
severity | TBD | The Splunk prescribed severity values: critical, high, medium, low, informational, unknown
severity_id | detail.severity | The original detection's severity rating
signature | detail.title | A human readable label of the detection
signature_id | detail.findingType | A machine readable label for the detection
src | TBD | The thing that caused the detected activity
src_type | TBD | The type of thing that caused the detected activity
tag | TBD | These will determine which datamodels this event is mapped to
type | "alert" | The alert type prescribed by the Splunk Alert datamode: alarm, alert, event, task, warning, unknown
user | TBD | A user involved in the detected activity in the format used by the Splunk ES Identity inventory. This can the actor or target: we have to choose what makes sense for our use-case.
user_name | n/a | A username invovled in the detected activity. Human readable.
vendor_account | account | The AWS where the activity took place
vendor_region | account.region | The AWS region where the finding was generated

### Parsing the Finding Type/Signature ID
GuardDuty provides a [*Finding Type* field](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_finding-format.html) in a machine parseable format that we will use as the CIM Alert *signature_id*. It contains a lot of detail that we may want to use during our mapping process. I use the following Splunk Regular Expression in *rex* to parse out it's parts.

`| rex field=detail.findingType "(?<ThreatPurpose>[^:]+):(?<ResourceTypeAffected>[^/]+)/(?<ThreatFamilyName>[^\.]+)\.(?<DetectionMechanism>[^!]+)!(?<Artifact>)"`

This will produce the fields *ThreatPurpose, ResourceTypeAffected, ThreatFamilyName, DetectionMechanism, Artifact* and we may or may not want to use these later when determining what other fields to map to the CIM Alert datamodel.

## Parsing the Finding Details
This is the tricky part. GuardDuty has many different types of findings and each one provides different details with different field names. There are thousands of them! How do we know which fields to parse?

For our purpose, we do not need every detail provided in a GuardDuty finding, we only need a few to map to the CIM Alert datamodel. Specifically:
- The source of the finding. Who was the actor? Was it an IP? An account?
- The target of the finding. What was affected by the actor? Was it an EC2 instance? An S3 bucket?

We may need a few other details to help provide us context and generate a human readable description.

The field names follow a well structured format defined by an API and easily parsible when exported in JSON. If we parse out relevent details about the type of finding and the resources affected, we can determine which detial fields we want to parse out as well.


## Dynamically Mapping GuardDuty Targets to CIM Destinations
The CIM uses *dest* to represent the thing that is affected by an event. GuardDuty findings call these *targets*. In the CIM Alert datamodel there is only one *dest* field, but we can describe it with the *dest_type* field. 




## Should we map GuardDuty Findings to other Splunk CIM Datamodels?
Yes. While all GuardDuty findings can be usefully modeled as Splunk Alerts, some GuardDuty findings can be mapped to other CIM Datamodels.

For examples:
- GuardDuty can data malware which maps to the CIM Malware datamodel.
- GuardDuty can detect network attacks which maps to the CIM Intrusion Detection datamodel
- GuardDuty can detect exfiltration which could map to the CIM DLP datamodel

If you use Splunk Enterprise Security (Splunk ES) then you will have immediate benefits. Splunk ES used many datamodels automatically in dashboard, correlation searches, and investigative tools. By mapping specific GuardDuty findings to relevant CIM datamodels used automatmatically improve your ability to gain insights.

However, if you are using Splunk Enterprise without Splunk ES, I think you have to carefully consider if you have a use case. You may get value from the datamodels, but only if you are already mapping other datasources to them, or if you are building your own add-ons, dashboards, alerting, or reporting.

## References

- [GuardDuty Finding Types](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_finding-types-active.html)
- [GuarDuty Finding Summar](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_findings-summary.html)
- [Splunk CIM Alert Datamodel](https://docs.splunk.com/Documentation/CIM/5.1.1/User/Alerts)
