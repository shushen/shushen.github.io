---
id: 290
title: Quite useful tool to handle large pcap files
date: 2010-09-16T00:43:52+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=290
permalink: /290
aktt_notify_twitter:
  - no
categories:
  - Computer
  - Networking
tags:
  - pcap
  - wireshark
---
Lately I&#8217;ve got a pcap file over 700MB to look at and Wireshark crashes when opening after 10 minutes of trying. So this pcap-util based on Perl Net::Pcap has been quite useful to filter out what I&#8217;m interested in, it&#8217;s also possible to divide the file according to the timeline if filter does not apply. Check it out [here](http://www.badpenguin.co.uk/files/pcap-util).
