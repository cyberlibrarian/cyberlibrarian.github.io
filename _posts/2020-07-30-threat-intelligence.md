---
layout: post
title:  "Threat Intelligence July 30 2020"
subtitle: "July 2020 Cybersecurity News"
authors: [michael,moro]
categories: [Moro and Mike]
image: assets/images/2020-07-30.png
youtube: cDB_WgxTLEM
tags: [featured, upcoming, youtube, livestream, cybersecurity, threat intelligence]
date: 2020-07-30 19:00:00
#mp3_file: assets/mp3/2020-07-16_Cybersecurity_Certifications.mp3
summary: Alec and Chris join Moro and Mike for a briefing on the latest threats and cybersecurity news for July 2020
#duration: "01:39:36" #audio length in min
#length: "93233572" #filesize in byte
explicit: "no" #other option is no
block: "no" #means is shown in itunes
---
Cybersecurity Analysts Alec and Chris are back to presents some of the latest cyber-threats and discuss cybersecurity news for July 2020.

Join us for a LIVE discussion and Q&A at the end. We will be discussing numerous aspects of the Twitter Hack and taking your questions.

## Michael's Notes

### MEOW Attack

Ilascu, I. \[July 22, 2020\]. New MEOW Attack has Wiped Dozens of Unsecured Databases. Bleeping Computer. 
: <https://www.bleepingcomputer.com/news/security/new-meow-attack-has-wiped-dozens-of-unsecured-databases/>

### Canadian Stories

n.a. \[July 6, 2020\]. Clearview AI ceases offering its facial recognition technology in Canada. Office of the Privacy Commissioner of Canada. 
: <https://priv.gc.ca/en/opc-news/news-and-announcements/2020/nr-c_200706/>

GENERAL. \[Jul 20, 2020\]. AMBROSE RESPONSE TO BLACKBAUD DATA BREACH. Ambrose University Website. 
: <https://ambrose.edu/ambrose-response-blackbaud-data-breach>

n.a. \[n.d.\]. Security Incident. Blackbaud Website. 
: <https://www.blackbaud.com/securityincident>

Wattpad. \[Jul 14, 2020\]. Statement Regarding Recent Security Issue. Wattpad Website.  
: <https://company.wattpad.com/blog/2020/7/14/statement-regarding-recent-security-issue>
: While wattpad says that passwords were not accessed, they later reveal enough detail to show that salted password hashes were accessed. They have not disclosed how the passwords were hashed, and that is probably reasonable. Oddly they have said what HAS NOT been accessed, but not what HAS BEEN accessed. Is that bad?

CANADIAN PRESS. \[Jul 20, 2020\]. Wattpad investigating possible data breach, won’t say how many may be impacted. Lethbridge Herald. 
: <https://lethbridgeherald.com/business/2020/07/20/wattpad-investigating-possible-data-breach-wont-say-how-many-may-be-impacted/>

### Emotet Infrastructure Hacked

Ilascu, I. \[July 24, 2020\]. Emotet malware operation hacked to show memes to victims. Bleeping Computer. 
: <https://www.bleepingcomputer.com/news/security/emotet-malware-operation-hacked-to-show-memes-to-victims/>

### Evil Corp / WastedLocker / Garmin Hack

Evil Corp is a threat actor dating back to 2007. They are associated with well known malware like Dridex and BitPaymer. You may recall headlines like “Dridex is back!” 
: <https://blog.talosintelligence.com/2014/12/dridex-is-back-then-it-gone-again.html>
: Evil Corp is using a new ransomware called WastedLocker. They were in the news this week because of a devastating breach of Garmin (the GPS maker). However, Synmatec had already reported and warned dozens of others that they were targeted and breach was imminent. Symantec claims their efforts stopped dozens of US companies before the ransomware was deployed.

The Evil Corp kill chain for these attacks looks like this:
- Javascript fake update
- Powershell to download stager
- Cobalt Strike Beacon + .Net Injector
- LOLBAS to obtain privilege escalation
- Disable Windows Defender
- (my speculation) LOLBAS to obtain Domain Admin
- PSExec to distribute WastedLocker across network
- Extortion 

Yapparova, L. \[Dec 12, 2019\]. The FSBs Personal Hackers. Meduza Website. 
: <https://meduza.io/en/feature/2019/12/12/the-fsb-s-personal-hackers>
: This article, overlooked in western press, offers a fascinating look at the people behind and evolution of Evil Corp. One member shut down their social media accounts when the authors contacted them via their lawyer for an interview.
: <https://symantec-enterprise-blogs.security.com/blogs/threat-intelligence/wastedlocker-ransomware-us>
: <https://www.bleepingcomputer.com/news/security/dozens-of-us-news-sites-hacked-in-wastedlocker-ransomware-attacks/>
: <https://www.bleepingcomputer.com/news/security/evil-corp-blocked-from-deploying-ransomware-on-30-major-us-firms/>
: <https://www.bleepingcomputer.com/news/security/garmin-outage-caused-by-confirmed-wastedlocker-ransomware-attack/>

Some claim Evil Corp is NOT exfiltrating data. But given the extortion they are demanding (tens of millions) I would not rule it out. <https://www.bankinfosecurity.com/evil-corps-wastedlocker-campaign-demands-big-ransoms-a-14497>

Complicating matters is that the people being Evil Corp are under indictment in the USA and paying the extortion demand may be a crime.

DopplePaymer, who does steal data during their extortion, started as people who split from EvilCorp (more information needed)

### Twitter Hack

Isaac, M., Frenkel, S., and Conger, K. \[July 17, 2020\]. Twitter Struggles to Unpack a Hack Within Its Walls. New York Times. <https://www.nytimes.com/2020/07/16/technology/twitter-hack-investigation.html

Barrett, B. \[July 18, 2020\]. Security News This Week: Who Pulled Off the Twitter Hack? WIRED Magazine. <https://www.wired.com/story/twitter-hack-suspect-vpns-securit-news/>

Krebs, B. \[July 16, 2020\]. Who’s Behind Wednesday’s Epic Twitter Hack? Krebs on Security. <https://krebsonsecurity.com/2020/07/whos-behind-wednesdays-epic-twitter-hack/>

Krebs, B. \[July 20, 2020\]. Twitter Hacking for Profit and the LoLs. Krebs on Security. <https://krebsonsecurity.com/2020/07/twitter-hacking-for-profit-and-the-lols/>

Cox, J. \[July 15, 2020\]. Hackers Convinced Twitter Employee to Help Them Hijack Accounts. Motherboard. <https://www.vice.com/en_us/article/jgxd3d/twitter-insider-access-panel-account-hacks-biden-uber-bezos>

Cox, J. \[July 16, 2020\]. After Twitter Hack, Senators Ask why DMs Aren’t Encrypted. Motherboard. <https://www.vice.com/en_us/article/jgxdwy/twitter-encrypted-direct-messages-dms-ron-wyden>

Maiberg, E. & Koebler, J. \[July 16, 2020\]. Twitter ‘Blacklists’ Lead the Company into Another Trump Supporter Conspiracy. Motherboard. <https://www.vice.com/en_us/article/n7wdxd/twitter-blacklists-lead-the-company-into-another-trump-supporter-conspiracy>

## Chris Notes

In conjunction with the Emotet network being hacked to show meme’s. Emotet had been dormant for five months prior to starting up again. 

O'Donnell, L. \[ July 21, 2020\]. Emotet Returns in Malspam Attacks Dropping TrickBot, QakBot. ThreatPost. <https://threatpost.com/emotet-returns-in-malspam-attacks-dropping-trickbot-qakbot/157604/>	
: Two potentially related pieces? Government orgs recommend immediate action to secure OT and ICS systems right after alleged Chinese hackers are indicted on multiple charges for stealing intellectual property. 

SANS News Bites (2020, July 24). CISA and NSA Urge ‘Immediate Action’ to Secure Critical Infrastructure Operations Technology and Control Systems. SANS. <https://www.sans.org/newsletters/newsbites/xxii/58>

SANS News Bites (2020, July 24). Alleged Chinese Hackers Indicted on Multiple Charges for Stealing Intellectual Property. SANS. <https://www.sans.org/newsletters/newsbites/xxii/58>
: More escalations of cyber attacks on real world infrastructure. Unknown attackers hit water pumps in Israel which required technicians to physically repair. Similar attacks were carried out earlier this year in April. This follows an alleged attack by Israel on an Iranian port facility in May.

TOI Staff (2020, July 17) Cyber attacks again hit Israel’s water system, shutting agricultural pumps. The Times of Israel.
<https://www.timesofisrael.com/cyber-attacks-again-hit-israels-water-system-shutting-agricultural-pumps/>

Warrick, J. (2020, May 8).  Foreign intelligence officials say attempted cyberattack on Israeli water utilities linked to Iran. The Washington Post
<https://www.washingtonpost.com/national-security/intelligence-officials-say-attempted-cyberattack-on-israeli-water-utilities-linked-to-iran/2020/05/08/f9ab0d78-9157-11ea-9e23-6914ee410a5f_story.html>

Warrick, J. (2020, May 18).  Officials: Israel linked to a disruptive cyberattack on Iranian port facility. The Washington Post
<https://www.washingtonpost.com/national-security/officials-israel-linked-to-a-disruptive-cyberattack-on-iranian-port-facility/2020/05/18/9d1da866-9942-11ea-89fd-28fb313d1886_story.html>

Discord API can be leveraged to compromise local machines. Just a point about “what is this local app exposing on my endpoint?”

Mertens, Xavier (2020, July 24). Compromized Desktop Applications by Web Technologies. SANS Internet Storm Center <https://isc.sans.edu/forums/diary/Compromized+Desktop+Applications+by+Web+Technologies/26384>

## Alec’s Notes

### Maze Cartel

<https://securityintelligence.com/news/ransomware-news-maze-gang-forms-extortion-cartel/>

### Avaddon Ransomware

<https://www.bleepingcomputer.com/news/security/new-avaddon-ransomware-launches-in-massive-smiley-spam-campaign/>

<
https://www.zdnet.com/article/this-botnet-has-surged-back-into-action-spreading-a-new-ransomware-campaign-via-phishing-emails/>

### APT-29 targeting Canadian COVID-19 Vaccine development

<https://www.securitymagazine.com/articles/92870-apt29-targets-covid-19-vaccine-development>
