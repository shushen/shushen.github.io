---
id: 82
title: First week of the year and a bug in Month Calendar Control of Windows
date: 2009-02-03T15:13:50+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=82
permalink: /82
categories:
  - Computer
---
The first week of the year is defined by [ISO
8601](http://en.wikipedia.org/wiki/ISO_8601#Week_dates):

> There are mutually equivalent descriptions of week 01:
> the week with the year's first Thursday in it (the formal ISO definition),
> the week with 4 January in it,
> the first week with the majority (four or more) of its days in the starting year, and
> the week starting with the Monday in the period 29 December – 4 January.

The designers at M$ of the Month Calendar Control of Windows may arbitrarily
picked one of the "equivalents":

> [Week 1 is defined as the first week that contains at least four
> days.](http://msdn.microsoft.com/en-us/library/bb760919(VS.85).aspx)

while they ignore that their pick is only true when [the first day of the week
is Monday](http://en.wikipedia.org/wiki/ISO_8601#Week_dates):

> The ISO week-numbering year starts at the first day (Monday) of week 01 and
> ends at the Sunday before the new ISO year (hence without overlap or gap).

This results in a non-ISO-compliant week number for the first week of 2009
(and, indeed, the whole year) as shown below if one uses the default setting of
the control to have Sunday as the first day of the week:

![Wrong week numbers due to setting Sunday as the first day of a
week](/assets/2009/01/screenshot.png)

But in fact it shall be like this:
![Correct week numbers by setting Monday as the first day of a
week](/assets/2009/01/screenshot1.png)


This issues shall exist as late as in the following version of Windows Common
Controls

> [5.82 Comctl32.dll Windows XP and Windows
> Vista](http://msdn.microsoft.com/en-us/library/bb776779(VS.85).aspx)

It can be reproduced on my machine with WinXP SP3 and comctl32.dll version
string "5.82 (xpsp.080413-2105)".

This might be named the Y2009 problem?
