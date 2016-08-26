---
id: 10
title: Configure inband DTMF for X-Lite
date: 2007-12-29T11:30:54+00:00
author: Shu
layout: post
guid: https://www.wavether.com/wp/?p=10
permalink: /10
categories:
  - Computer
  - VoIP
tags:
  - dtmf
  - sip
  - VoIP
  - x-lite
---
[X-Lite](http://www.counterpath.com/xlite-overview.html) can send 3 different types of DTMF, and you need to know which to use or to try all methods:

  * In-band DTMF
  * RTP telephone-event per [RFC 2833](http://tools.ietf.org/html/rfc2833)
  * SIP INFO per [RFC 2976](http://tools.ietf.org/html/rfc2976)

This is the most likely solution:
  
Dial \***7469 (send)

Once you get the advanced options menu up, filter first for DTMF. Find the Force Inband DTMF entry, and change the value accordingly.

Then filter for 2833. Find the RTP 2833 enabled line, and change this value accordingly.

Setting both to 0 will force DTMF as SIP_INFO

<!--adsense-->
