---
layout: post
title:  "NEW Windows 10 Packet Sniffer"
authors: [michael]
categories: [ Technical Tuesday ]
image: assets/images/2020-05-19.png
youtube: 1sJSKWkhh7k
tags: [featured,windows,windows10,packet-sniffer,pktmon]
---
This Tuesday I will demonstrate "pktmon" the new Windows 10 packet sniffer. It is built-in to the latest release of Windows 10 and promised to be the new great way to get packet captures.

It won't replace Wireshark for decoding packets and it does not yet have real-time support but the filter system is useful.

Bleeping Computer has an article that explores pktmon's commands and use:      
  <https://www.bleepingcomputer.com/news/microsoft/windows-10-quietly-got-a-built-in-network-sniffer-how-to-use/>

No Spaceships has an article explaining how to use Powershell to get PCAPs on Windows 10:
  <https://www.nospaceships.com/2018/09/19/packet-capture-on-windows-without-drivers.html>

The old ETL2PCAPNG program, whose capability will be added to PKTMON in May 2020 is here: 
  <https://github.com/microsoft/etl2pcapng>

My Quick Reference card for PKTMON is in github: 
  <https://github.com/cyberlibrarian/pktmon-quick-reference.git>
