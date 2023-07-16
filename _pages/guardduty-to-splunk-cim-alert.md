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

The general JSON structure of a [GuardDuty finding from CloudWatch](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_findings_cloudwatch.html) looks like this. But we only care about what is in the *detail* field.

```
{
         "version": "0",
         "id": "cd2d702e-ab31-411b-9344-793ce56b1bc7",
         "detail-type": "GuardDuty Finding",
         "source": "aws.guardduty",
         "account": "111122223333",
         "time": "1970-01-01T00:00:00Z",
         "region": "us-east-1",
         "resources": [],
         "detail": {GUARDDUTY_FINDING_JSON_OBJECT}
}   
```

You can see a sample of the *details* object on the [AWS GuardDuty Response Syntax](https://docs.aws.amazon.com/guardduty/latest/APIReference/API_GetFindings.html#API_GetFindings_ResponseSyntax) page. Here is a sample:

```
{
  "account: ...,
  "detail": {
    "id": ...,
    "type": ...,
    "resource": {},
    "service": {},
    "severity": 3.3,
    "createdAt": ...,
    "updatedAt": ...,
    "title": ...,
    "description": ...
  }
  "detail-type": "GuardDuty Finding",
  "id": ...,
  "region": "us-east-1",
  resources: [],
  source: "aws.guardduty",
  time: ...,
  version: 0
}
```

You can see [an example from the *aws-samples/amazon-guardduty-waf-acl* GitHub repository](https://github.com/aws-samples/amazon-guardduty-waf-acl/blob/master/templates/gd2acl_test_event.json). It shows all the fields you might expect for one specific type of finding. The fields vary from finding type to finding type.

### Parsing the Finding Overview
The GuardDuty Finding overview contains descriptive metadata to help us understand the type of finding, how it was detected, who the actor was, and was resource was affected. The finding overview data fills in most of the CIM Alert fields.

| CIM Alert Field | GuardDuty Finding Field | Description |
|-----------------|-------------------------|-------------|
| app | source | When you have many alert sources in the CIM datamodel, you need this to find the GuardDuty ones. |
| description | detail.description | A human readable description of the details of the alert.
| dest | TBD | The thing affected by detected activity |
| dest_type | TBD | The type of thing affected by the activity detected |
| id | detail.id | A unique ID for this specific occurence of the detection type. Updates or related details will share this ID |
| mitre_technique_id | TBD | We could create a lookup table to perform this mapping |
| severity | TBD | The Splunk prescribed severity values: critical, high, medium, low, informational, unknown |
| severity_id | detail.severity | The original detection's severity rating |
| signature | detail.title | A human readable label of the detection |
| signature_id | detail.type | A machine readable label for the detection |
| src | TBD | The thing that caused the detected activity |
| src_type | TBD | The type of thing that caused the detected activity |
| tag | "alert" | These will determine which datamodels this event is mapped to |
| type | "alert" | The alert type prescribed by the Splunk Alert datamodel: alarm, alert, event, task, warning, unknown |
| user | TBD | A user involved in the detected activity in the format used by the Splunk ES Identity inventory. This can the actor or target: we have to choose what makes sense for our use-case. |
| user_name | n/a | A username invovled in the detected activity. Human readable. |
| vendor_account | account | The AWS where the activity took place |
| vendor_region | region | The AWS region where the finding was generated |

## Parsing the Finding Details
This is the tricky part. GuardDuty has many different types of findings and each one provides different details with different field names. There are thousands of them! How do we know which fields to parse?

For our purpose, we do not need every detail provided in a GuardDuty finding, we only need a few to map to the CIM Alert datamodel. Specifically:
- The source of the finding. Who was the actor? Was it an IP? An account?
- The target of the finding. What was affected by the actor? Was it an EC2 instance? An S3 bucket?

We may need a few other details to help provide us context and generate a human readable description.

The field names follow a well structured format defined by an API and easily parsible when exported in JSON. If we parse out relevent details about the type of finding and the resources affected, we can determine which detial fields we want to parse out as well.

### Parsing the Finding Type/Signature ID
GuardDuty provides a [*Finding Type* field](https://docs.aws.amazon.com/guardduty/latest/ug/guardduty_finding-format.html) in a machine parseable format that we will use as the CIM Alert *signature_id*. It contains a lot of detail that we may want to use during our mapping process. I use the following Splunk Regular Expression in *rex* to parse out it's parts.

```
| rex field=detail.findingType "(?<ThreatPurpose>[^:]+):(?<ResourceTypeAffected>[^/]+)/(?<ThreatFamilyName>[^\.]+)\.(?<DetectionMechanism>[^!]+)!(?<Artifact>)"`
```

This will produce the fields *ThreatPurpose, ResourceTypeAffected, ThreatFamilyName, DetectionMechanism, Artifact* and we may or may not want to use these later when determining what other fields to map to the CIM Alert datamodel.

### Mapping GuardDuty Severity to CIM Alert Severities
GuardDuty severities to map completely to Splunk CIM's Alert datamodel. You will need to make a design decision and below you can see my choices.

GuardDuty currenlty uses a 0-10 numeric value and maps these to *low*, *medium*, *high*. However, they do not use the numeric values 0-1 or 9-10. Further, GuardDuty's documentation recommends "that you treat any High severity finding security issue as a priority and take immediate remediation steps to prevent further unauthorized use of your resources." CIM Alert uses *critical*, *high*, *medium*, *low*, *informational*, and *unknown*. 

How should we map GuardDuty severity to CIM Alert severity? I use the following table and only deviate from GuardDuty's mapping of numeric ratings to word labels to put the highest GuardDuty findings as Splunk CIM "critical". I make an assumption that GuardDuty will only use 1 decimal place.

| GuardDuty | CIM Alert | Comment | 
|-----------|-----------|---------|
| 0-0.9 | informational | Unused by GuardDuty |
| 1-3.9 | low | Failed attempts |
| 4 - 6.9 | medium | Suspicious and anomylous activity |
| 7-7.9 | High | We will stick with the GuarDuty definition here |
| 8-10 | Critical | Based on my experience | 

A simple Splunk eval to acheive this:

```
| eval severity=case(
    detail.severity > 7.9, "critical",
    detail.severity > 6.9, "high",
    detail.severity > 3.9, "medium",
    detail.severity > 0.9, "low",
    detail.severity > -1, "informational"
)
```

## Dynamically Mapping GuardDuty Targets to CIM Destinations
The CIM uses *dest* to represent the thing that is affected by an event. GuardDuty findings call these *targets*. In the CIM Alert datamodel there is only one *dest* field, but we can describe it with the *dest_type* field. 

There are several CIM Alert fields that are still *To Be Determined* (TBD). We must use additional details from the GuardDuty finding to determine the values we need.

| CIM Alert Field | GuardDuty Finding Field | Description |
|-----------------|-------------------------|-------------|
| dest | TBD | The thing affected by detected activity |
| dest_type | TBD | The type of thing affected by the activity detected |
| mitre_technique_id | TBD | We could create a lookup table to perform this mapping |
| severity | TBD | The Splunk prescribed severity values: critical, high, medium, low, informational, unknown |
| src | TBD | The thing that caused the detected activity |
| src_type | TBD | The type of thing that caused the detected activity |
| user | TBD | A user involved in the detected activity in the format used by the Splunk ES Identity inventory. This can the actor or target: we have to choose what makes sense for our use-case. |
| user_name | n/a | A username invovled in the detected activity. Human readable. |

The values we want are usually found in the GuardDuty *resource* details. Some of them might be in the *service* details. However, these are complex data objects with many fields. We may need to combine them or compare other field values to determine the specific one we need.

### Understanding GuardDuty Resource Details

Each GuardDuty finding detail will contain a *resource* but is this the thing that was the target or the source of the detected activity? Is the threat actor or the victim?

We can determine this by look at the *service* details. This is contains details of what the GuardDuty service observed and how to interpret them.

Relevant parts can be
```
detail.service.resourceRole == TARGET
detail.service.action.actionType = <actionTypeParseable> (eg. NETWORK_CONNECTION)
map actioneTypeParseable to actionType
detail.service.action.<actionType>Action
detail.resource.resourceType == <resourceType>
detail.resource.<resourceType>Details

detail.resource.accessKeyDetails.accessKeyId
detail.resource.accessKeyDetails.principalId
detail.resource.accessKeyDetails.userName
detail.resource.accessKeyDetails.userType

detail.resource.containerDetails

detail.resource.ebsVolumeDetails
detail.resource.ebsVolumeDetails.scannedVolumeDetails.deviceName
detail.resource.ebsVolumeDetails.scannedVolumeDetails.volumeArn

detail.resource.ecsClusterDetails
detail.resource.eksClusterDetails

detail.resource.instanceDetails
detail.resource.instanceDetails.imageDescription
detail.resource.instanceDetails.instanceId
detail.resource.instanceDetails.networkInterfaces{}.privateIpAddress
detail.resource.instanceDetails.networkInterfaces{}.publicIp

detail.resource.lambdaDetails
detail.resource.rdsDbInstanceDetails
detail.resource.rdsDbuserDetails

detail.resource.s3BucketDetails
detail.resource.s3BucketDetails.arn
detail.resource.s3BucketDetails.name
detail.resource.s3BucketDetails.owner.id
detail.resource.s3BucketDetails.type
```

We can easily map the dest_type and src_type from *detail.service.resourceRole* and *detail.resource.resourceType*.

```
| eval dest_type=case(detail.service.resourceRole=="TARGET", detail.resource.resourceType, True, "unknown")
| eval src_type=case(detail.service.resourceRole=="ACTOR", detail.resource.resourceType, True, "unknown")
```

It is more challenging to determine the specific value we should put in src or dest however. The following table can be used to describe how we choose values to put into src, dest, user, and user_name. It should have one value for each combination of resourceType and resourceRole. We may need to include a column for the *finding type*, *threat family name*, *detection mechanism* as well. If so, this will be quite long and may need to be updated overtime as we encounter findings we have not handled. 

| Resource Type | Resource Role | dest field | src field | user field |
|---------------|---------------|------------|-----------|------------|
| accessKey | TARGET | detail.resource.accessKeyDetails.accessKeyId | TBD | detail.resource.accessKeyDetails.principalId |
| instance | TARGET | detail.resource.instanceDetails.instanceId | | TBD |
| ebsVolume | TARGET | detail.resource.ebsVolumeDetails.scannedVolumeDetails.deviceName | TBD | TBD |

## Enriching the Alert Description
We have an opportunity to enrich the CIM Alert *description* field by combining the GuardDuty *description* with other information. The *description* field provided by GuardDuty is fine, but relatively generic. Most of the details GuardDuty provides are in other fields. For any important information we want our Splunk users to see but for which CIM Alert has not field, we should consider adding it to the *description* field.

Another approach is to noralize GuardDuty events to multiple CIM datamodels, some of which can represent the details of GuardDuty alerts better than others. This is discussed in the *Conclusion* of this article.

What could we add to the description?

- Attack Details
- Malware family details
- Quarantine status
- Threat intel used to determine the finding
- Additional 'src' and 'dest' values we chose not to use in our mapping
- AWS identifiers that would help an analyst quickly lookup more details
- Links to GuardDuty


## Conclusion 
Mapping a complex detection alert to a the CIM Alert fields requires us to make design decisions that interpret the intention of both systems. For example, what is the intended meaning of *critical* in labeling an alert? Our design choices will affect how the normalized data is used later.

Further, it takes analysis to determine which data represents the threat actor, action, and impacted asset. In this excercise, both models have presentations for these, but mapping this is not straight forward. We have learn about how each format intends to represent them and transform one into the other, often comparing and combining multiple fields.

### Should we map GuardDuty Findings to other Splunk CIM Datamodels?
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
