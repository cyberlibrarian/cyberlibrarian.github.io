---
published: false
layout: post
title:  "Investigating DNS and IP Addresses"
summary: "In Security Operations we frequently have to investigate DNS and IP addresses to determine if they are known threat or to attribute them to some activity or owner. This article contains a list of free, trial, or open-source resources for performing address analysis."
authors: [michael]
categories: [ Blog ]
tags: [threat-intelligence,security-operations,investigations,ip-address,dns]
---
{{ page.summary }}

## NOTE: 2023-03-18

I'm publishing this early so Emily and others can get a list of resources. I will be making frequent updates over the next few weeks. Expect poor organization. Enjoy!

## What can DNS and IP Addresses tell us?

When you are investigating a security event, you often when to know more about the DNS and IP addresses involved. For examples:
- Your server received a brute-force password guessing attack on SSH and you know the IP address of the attacker.
- A suspicious process was detected on an employee's laptop and you have a list of all DNS requests that laptop has made.
- You have discovered malware that was sent to a VIP and you want to know what that malware would have done. You extract a series of IP address and DNS names that were embedded in the malware.
- An employee receives a phishing email containing a link to a website. You have the URL which includes the DNS name of the server.
- An employee clicked on a innocent looking link, but was redirect multiple times before being directed to a fraudulent imposter site. You have the DNS names of all the redirect sites.

In all of these cases you may want to assess whether the IP or DNS names represent a threat, or are simply "normal". Frequently, you may want to attribute the threat to a known threat actor or campaign. Has anyone else ever seen that IP address or DNS name?

DNS and IP Address intelligence can tell us:
- if anyone has seen those addresses and if they have been associated with malicious or non-malicious activity.
- who "owns" the address, and often if there were recent changes to the address or it's ownership.
- if there are other addresses associated with the one you are interested
- the country or city associated with the address
- the ISP that is hosting the systems the address represents
- the abuse and reporting contacts for the address

## Passive DNS

Passive DNS refers to collections of historic DNS records. DNS can change frequently. Today www.cyberlibrarian.ca might be IP address 1.2.3.4 but tomorrow it might an alias (CNAME) for evil.cybrarian.ca. Or it might even be deleted all together.

Passive DNS will show us a history of all the changes to the DNS records. 

Passive DNS can help us discover other DNS records for a domain we are investigating. For example, imagine you observed the DNS name "evil.cybrarian.ca" but want to know if there are other DNS names for "cybrarian.ca". Passive DNS can tell you.

Most Passive DNS services are commercial and can be costly. However, there are free, trial, and open-source versions:

### Passive DNS Free Trials
I am grateful for these vendors who offer a "free tier". How do you know if you need Passive DNS services? Being able to learn how to benefit from them with hands-on experience is a great form of marketing! Yes, they have limits, but for learners these are great.

- [RiskIQ Community](https://community.riskiq.com/login)
-- RiskIQ has always had a free option that gives you limited access to their great dataset. You can get some history for IPs and DNS names, but it won't got back that far. It's quite useful even with the limits. 
- [Iris Investigate](https://www.domaintools.com/products/platform/iris-investigate/) from DomainTools
-- DomainTools has other useful DNS intelligence offerings. Iris includes DNS intelligence and risk scoring. Is that IP evil? The risk score can tell you. 
- [SecurityTrails](https://securitytrails.com/)
-- You get 50 queries per month for free. Historic DNS records, domain and IP data. Suitable for experiments, learning, and causual investigations.


## References

- [How to Perform Threat Hunting with Passive DNS](https://securitytrails.com/blog/threat-hunting-using-passive-dns)
-- A detailed set of instructions for using SecurityTrails API, with simple-to-execute CLI commands (curl) to get JSON data.
