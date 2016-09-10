---
title: Securing email of your domain against spam and phishing
author: Shu
layout: post
categories:
  - Computer
  - Networking
tags:
  - email
  - google
  - spf
  - dmarc
  - dkim
---

Securing email of your domain against spam and phishing has two aspects:

 1. You need an authentication key to sign all outgoing emails
 2. You need publish via DNS records the public key of the authentication key,
along with policies about who can send for your domain and what others should
do if they receive unauthenticated emails from your domain.

Hosting email of your domain on Google Apps makes things pretty easy to
authenticate your emails, prevent spammers and phishing. But you'll need a good
DNS provider as well to support provisioning a number of DNS records.

Below are three articles from Google Apps that covers what you need do - they
are not limited to Google Apps hosted emails and could be very informative in
general:

 - [Authenticate email with DKIM](https://support.google.com/a/answer/174124).
   This tells you how to enable Google Apps email authentication and publish the
public key in a DNS TXT record for DKIM

 - [Identify spam messages with SPF
   records](https://support.google.com/a/answer/33786). This is about how to
create a DNS TXT record for SPF policy to help receiver identify spammers from
your authorized sender or email gateway.

 - [Prevent outgoing spam with
   DMARC](https://support.google.com/a/answer/2466580). This describes the DNS
TXT record for DMARC that publishes your desired policy of how the receiver
shall deal with unauthenticated emails from your domain if the email does not
pass SPF and DKIM check.

Finally, when you've done all your settings, use [Google Apps Toolbox - Check
MX](https://toolbox.googleapps.com/apps/checkmx/) to validate your domain's MX
records.
