---
published: true
layout: post
title:  "Documenting Your Cybersecurity Investigations (First Draft)"
summary: "This article provides guidance on how to document a case in security operations. When you triage security events, investigate something suspicious, or respond to an incident, what you record is important. It provides evidence that your investigation was thorough, accurate, and correct. For complicated incidents, your notes support your team. They also allow others to learn from your past work."
authors: [michael]
categories: [Blog]
image: https://www.splunk.com/content/dam/splunk-blogs/images/en_us/2024/11/workflows-hero.png
tags: [secops,security-operations,documentation,writing,case-management,incident-reporting,case-notes]
date: 2025-02-23 14:53:00
---
{{ page.summary }}

# Introduction
There are many benefits to making a written record of our your cybersecurity investigations. You record does not need to be long or complicated, but by including the right information you can help yourself and your team.

# Why keep good investigation records?

The most important reason is to support *continuity of operations*. Your records help you and your team work effectively even with hour-to-hour disruptions. 

Your records need to have enough detail of your _observations, findings, and actions_ that you or your team can continue if you are interupted.

These are the scenarios that your records will benefit the most:

- coordinate complex investigation involving multiple people
- hand an investigation off to another analyst if you are called away or go home
- resume your investigation if you are interupted and need to return to it later
- verify your anaysis or actions in a threat recurrs unexpecedtly

> **_Note:_** We often think of continuity of operations as related to big disruptions: the kind that prevent you from using your systems or moving to an out-of-band or backup system. However, in Security Operations, we are faced with dozens of interuptions a day that disrupt our hour-to-hour operations.

## Traditional reasons for keeping good records
We should not overlook the reality that eventually, sometimes frequently, auditors and other analysts will need to review our records. There are consquences to not keeping adequate records. If your investigative notes are missing, you will be asked to *more* work, not less. That will prevent you from doing the work you enjoy and tie you up in meetings. Worse, if you investigative records are found lacking, there may be an over-reaction asking you to keep unecassarily exhaustive records in the future. It is better to get it right the first time.

Some common reasons to keep good records are:

1. *Compliance, legal, and regulatory requirements*: 
    - Many industries, such as healthcare, finance, and government, have regulations that mandate the documentation of security incidents.
    - Keeping thorough records ensures compliance with these regulations. In the event of a security breach, having thorough records can help organizations demonstrate due diligence and mitigate potential liabilities. 
    - Good record-keeping is essential for responding to legal requests, such as subpoenas or court orders, and for passing audits by regulatory bodies.
1. *Continuous improvement and learning*: 
    - Regular review of investigation records helps identify vulnerabilities and areas for improvement, allowing organizations to refine their security controls and procedures. 
    - By documenting the investigation process, organizations can identify areas for improvement and implement changes to prevent similar incidents from occurring in the future. 
    - Documented investigation records can serve as a knowledge base for training new analysts and improving overall cybersecurity skills within the organization.
1. *Detection engineering and cyber threat intelligence*: 
    - Detailed records help identify patterns and trends in cyber threats, enabling organizations to improve detection or blocking of future incidents. 
    - Sometimes the nature of a threat is only known later, and cyber threat intelligence can tell us more by reviewing details of recent investigations that are closed.
    - Detection engineering and cyber threat intelligence help incident response, and our good records enable them to help us.

Understanding the actions that will be taken needs to be coordinated. When there are multiple 
people involved and multiple systems, coordinating becomes critical. Centralized tracking is 
best (see Section 8.4 for more on incident case management), to ensure responders can 
reference the work done, and access data across activities. Above all, SOCs should avoid 
a system where responders maintain their own spreadsheets of indicators, actions, and 
artifacts. Spreadsheets limit the ability to coordinate, inhibit incident reporting, and can lead 
to misfires and misunderstandings. A tracking system should minimally capture the following:
 • Incident summary and details
 • Timeline
 • Incident responder lead and contact information
 • Actions completed and in process
 • Status
 If the SOC deems it necessary to break down specific findings, indicators, and adversary actions 
into a spreadsheet or similar tool, it is critical that all team members, including supporting 
IT personnel, snap to a consistent set of data capture and vetting, and all have the access 
when they need it. Above all, responding to incidents is most effective when following plans 
Strategy 5: Prioritize Incident Response | 141
and procedures. Stay true to incident plans and standard operating procedures throughout 
response, and update with lessons learned when the heat of response simmers down.


## A note on audit and regulatory requirements
Some analysts do not respect the value audit and assessment plays in cybersecurity. Why should the auditor's requirements matter? We did the work, nothing bad happened. Other analysts misinterpret requirements for auditability and assume they have to keep incredibly detailed records. 

The easier you make reviewing your incident records for auditors, the more time you have to conduct your work and improve your skills. Bad records mean more time spent in needless meetings. Good records mean, auditors understand your work and can easily verify you have met your requirements.

In the case of serious incident, lawyers may need to review your records. If you have poor records they may want to obtain countless details to verify they have not missed anything. Good records save you hassle.

You should always assume that someone like yourself will be asked to look at your incident records *without your assistance* and under time pressure. Could you understand what happened based on your incident record alone? If so, you've done enough.

# What to include in your investigation record

Well-documented records provide a clear trail of evidence, allowing investigators to reconstruct events and analyze the root cause of an incident. Your records need to have enough detail of your _observations, findings, and actions_ that you or your team can continue if you are interupted.

Your *observations* include simple things like the source of the detection, alert, or problem report. It also includes observables that you found relevant to your analysis. What did you see? 

Your *findings* are your conclusions based on what you observed. This is your analysis. Did you determine than an IP address was malicious? If so, say that, but also explain concisely *why*. It should be possible for someone else to read your note and come to the same conclusion.

Your *actions* are what you decided to do. What resolved the incident? Did you block an IP? Disable an account? Quarantine a system? You need to record what you decided to do, and provide evidence of how you did it. For example, did you block an IP by opening a ticket in ServiceNow for the your network team to reconfigure the firewall? Or did you do it yourself by logging into a system and adding the IP to a list? Someone else should be able to know what you changed and how you changed it.

If you include brief *observations*, *findings*, and *actions*, then someone like you should be able to review your record and undertand what occured, your conclusions, and verify the actions your took.

If you get interrupted in the middle of an investigation then you, or someone else, should be able to continue where you left off without your help.

## Triage
In the first few minutes you should determine if you think the event is worth further investigation and, if so, what kind of threat it *appears to be*.

- "This appears to be a suspicious email."
- "This appears to be malware downloaded from a website."
- "This appears to be an impersonation of our CEO by SMS."
- "This appears to be spam."

If you believe this is worth further investigation, note who you are assigning the investigation to.

- "I am assigning this to myself for further investigation."
- "I am escalating this to my supervisor for assignment."

## Identification
This is where your most important notes will be. You will record both your *observations* and your *findings* at this stage. You should collect and preserve evidence (observations) but also provide concise explanation of your analysis and conclusions. 

There are always two things that have be identified:
1. Identify the Impact
    - List the impacted assets and identities
    - Characterize the type of impact
1. Identify the Threat
    - Attribute the threat based on an indicator (IP, domain, email, file hash)
    - Attribute the threat to a campaign, threat actor, tool, or TTP

### Identifying Impact

You should make a list of the systems, computers, and people that were impacted. You can update this if your investigation expands. Make sure to record technical indicators such as IP addresses, hostname, email address, employee names etc. 

You also have to characterize the impact. What type of impact occured? How bad was it? 

For examples:
- "A single employee was flooded with thousands of spam messages. They are unable to use their email until it is resolved."
- "Malware was found on a server. It is unclear if data has been exfiltrated."
- "A single employee's account was compromised. Their email was accessed from an IP in Russia. We have not assessed how many emails were downloaded but we assume their contacts, and all emails are potentially lost. Further, the threat actor appears to have sent out 15 phishing emails to our business partners. A list is attached."
- "An employee in marketing downloaded and ran malware which made changes to their laptop before being blocked."

### Identifying the Threat
This is where you will record technical indicators such as attacker IP addresses, email address, domain names, and malware file hashes. 

You may also attribute the threat to a specific category, campaign, threat actor, tool, or TTPs. Ideally, you should be recording the MITRE ATT&CK techniques before your investigation is closed. 

"The attacker IP was 1.2.3.4. This appears to belong to a Russian company and in our threat intelligence is associated with other attacks."
"The phishing email came from bob@compromised.com, one of our partners. Copies of the phishing email are attached and screenshots of the phishing site are provided. It appears to be an adversary-in-the-middle phishing attack."
"The malware downloaded is believed to be SocGholish (medium confidence) based on the file hash and identification in our sandbox. Sample are attached as are screenshots of the website where it was downloaded from."
"I have attached the employees browser history. It shows that the malware came from an malvertising site that impersonated 7zip. Screenshots are attached. There are 4 domains listed that are all malicious."

### Timeline
Unless the incident is common and simple, you should immediately begin a timeline. As you gather more observations and take actions, you should not them with the precise time. This can include raw event records or observations you gather from people.

It helps to have a single note that you update as you go along. However, it is sufficient to add multiple notes, in real-time, and put your observations in. You can always write a summary later. But keeping this information where nobody but you can access it is unacceptable. If you our interupted, someone else will have to continue your investigation. The timeline is frequently the fastest way to get up-to-speed on an investigation.

## Containment & Eradication
This is where you will record any actions you take to contain a threat. You also need to include details *how* you executed those actions. You may want to explain *why* you took the action.

"Following standard operating procedure for detected malware, I will netcontain the laptop."
"I used Crowdstrike to netcontain the laptop at 10:35 UTC"
"Because the brute force attack is ongoing, I will block the IP address."
"At 10:35 UTC I put in a ServiceNow ticket (REQ20584) to have the IP blocked on our firewalls. I contacted to the supervisor for network at 10:41 UTC who said they would expededite the request immediately."
"Given that there are 15 domains in this phishing campaign but there have been no new detections today, I have added them all to the threat intelligence platform and tagged them for automatic blocking."
"I have disabled the employee's user account temporarily (10:35 UTC) until I can speak with them. I have notified their supervisor by email at 10:41 UTC."

It is far easier to do this as a running log in real time than to add these notes back later.

## Recovery
As an incident response analyst you are unlikely to carry out recovery activities. Perhaps you and re-enable accounts you have disabled, or release systems that you quarantined. However, activities like restoring from backup, re-imaging devices, or rebuilding a system from scratch are carried out by other teams.

You are still responsible for tracking that those activities occur, and ensure they are done in a secure way. Even if *you* do not carry out the recovery activities, you should include what recovery actions are planned and carried out. Ask for ticket numbers, and track the timeline precisely.

## Lessons Learned and Recommendations
Where there things you learned? Was there anything that prevented you from fully investigating the incident? Was there evidence that you could not obtain? Should improvement be made to address this type of incident?

Write them up. Your supervisor, detection engineering, or cyber threat intelligence will thank you.

## Post-incident Summary
You should always write a summary at the end of your investigation. It should only be a paragraph or two. It should state:
1. What the threat was determined to be.
2. The impact of the incident.
3. What actions were required to resolve the incident.
4. If there were any recommendations made.

- "An employee in claims downloaded malware from a website they found while seaching google. The malware executed but was blocked after it made changes to the registry. The laptop was netcontain and scheduled for re-imaging. The employee's leaders have been notified and ERM near-miss report has been filed."
- "The email was determined to be non-malicious: just spam. We updated the employee and thanked them for their report. No further action was required."
- "A partner notified us that their account had been used to send malicious emails. We investigated and found 13 employees had received phishing emails from the partner. 5 were blocked, 3 opened the email before we could quarantine the emails. No employees provided their credentials and no data was lost. We executed our 3rd party incident playbook, notified the business leader, and received a report by email explaining what happened. They did not have MFA on their O365 accounts leading to a single account takeover. No suspicious activity from the partner was found in systems."

# References
[^1]: https://www.splunk.com/en_us/blog/learn/open-cybersecurity-schema-framework-ocsf.html
[^2]: Knerler, K., Parker, I., & Zimmerman, C. (2023). *[11 strategies of a world-class cybersecurity operations center]. MITRE. (https://www.mitre.org/sites/default/files/2022-04/11-strategies-of-a-world-class-cybersecurity-operations-center.pdf)
