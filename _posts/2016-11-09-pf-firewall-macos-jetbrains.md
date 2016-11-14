---
title: Using Packet Filter (pf) firewall to block outgoing traffic on macOS
author: Shu
layout: post
categories:
  - Computer
  - Networking
tags:
  - macos
  - firewall
  - jetbrains
  - pycharm
  - packet
  - filter
  - security
  - privacy
---

Recently I found out that [PyCharm](https://www.jetbrains.com/pycharm/) from
[JetBrains](https://www.jetbrains.com/), despite being a wonderful IDE for
Python, is continuously broadcasting my username to `230.230.230.230` for
license check, see
[here](https://resharper-support.jetbrains.com/hc/en-us/community/posts/206730875%E2%80%94240-License-check)
for a report of the same problem for another Jetbrains' product, which has the
same underpinning IDE as PyCharm.

Naturally, I want a firewall to block the outgoing traffic to avoid leaking my
private information to any network I might connect to.

The OS X application firewall (see [Apple
notes](https://support.apple.com/en-ca/HT201642)) can block incoming traffic on
per-application basis and prevent applications from listening on network ports,
but unfortunately it cannot be configured to block outgoing traffic.

The application firewall, however, is indeed implemented with [Packet
Filter](https://www.openbsd.org/faq/pf/index.html) from
[OpenBSD](https://www.openbsd.org) project. Remember Mac OS X is part of the
BSD family? PF has been shipped with recent releases of Mac OS X since Lion,
including macOS since Sierra.

There are a number of third-party applications/firewalls on the market such as
[murus](http://www.murusfirewall.com/). But they basically provide the user a
GUI to configure PF on macOS - of course sometimes with other useful features
as well - and they are mostly paid application (although murus does have a
_lite_ version that is free).

But if you're comfortable with command line as I am, all GUI applications are
overkill for the problem in hand. It's possible to configure PF to block
outgoing traffic in several easy step and less than a few minutes!

1. First, create a new _anchor_ file named `/etc/pf.anchors/jetbrains` with the
following PF rule to block traffic on interface `en0` for any traffic sent to
IP multicast address `230.230.230.230`:

        $ cat /etc/pf.anchors/jetbrains
        block drop log quick on en0 from any to 230.230.230.230

    You would need _sudo_ privillege to create file under `/etc/pf.anchors`. An
anchor file is used to hold a sub-ruleset, which we will attach to the main PF
ruleset in the next step. `quick` asks PF to stop further processing should a
packet matches the rule. See PF filter reference on the [syntax of the
rules](https://www.openbsd.org/faq/pf/filter.html) for more details.

2. Then add the `jetbrains` anchor to the default PF configuration file
`/etc/pf.conf`. This allows the anchor and the rules to be active whenever you
activate the macOS firewall without interfering with any application firewall
rule you might have defined through GUI.

        $ cat /etc/pf.conf
        #
        # Default PF configuration file.
        ...
        # See pf.conf(5) for syntax.
        #

        #
        # com.apple anchor point
        #
        scrub-anchor "com.apple/*"
        nat-anchor "com.apple/*"
        rdr-anchor "com.apple/*"
        dummynet-anchor "com.apple/*"
        anchor "com.apple/*"
        load anchor "com.apple" from "/etc/pf.anchors/com.apple"

        #
        # jetbrains anchor point
        #
        anchor "jetbrains"
        load anchor "jetbrains" from "/etc/pf.anchors/jetbrains"

3. Last, start the firewall from `System Preferences`&#x2192;`Security & Privacy`
&#x2192;`Firewall`.

Tested with the following software versions:

 - macOS 10.12 (16A323)

Other useful resource for PF on macOS:

 - [Using pf on OS X Mountain
   Lion](http://blog.scottlowe.org/2013/05/15/using-pf-on-os-x-mountain-lion/)

    This article is mostly still relevant for macOS Sierra, although I believe
there is no need to create a launchd item should you put the anchor into the
default pf configuration file `/etc/pf.conf` as shown here.

 - [PF on Mac OS X](https://pleiades.ucsc.edu/hyades/PF_on_Mac_OS_X)

   This is a detailed wiki about PF and its command line `pfctl` and `pflog`
etc. Good read if you'd like to see more example usages of these tools.

 - [macOS Security and Privacy Guide](https://github.com/drduh/macOS-Security-and-Privacy-Guide#kernel-level-packet-filtering)

   This is a great guide with discussion of security and privacy on macOS to a
broad extent. It also touches packet filter and discusses options for
third-party firewalls (including options that may not use PF).
