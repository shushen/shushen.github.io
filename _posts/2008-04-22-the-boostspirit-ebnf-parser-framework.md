---
id: 30
title: The Boost:Spirit EBNF parser framework
date: 2008-04-22T16:53:31+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=30
permalink: /30
categories:
  - Computer
tags:
  - metaprogramming
  - networks
  - protocols
---
Came cross this library when searching for ideas to parse ABNF-based protocols (such as SIP and SDP).

> Spirit is an object oriented recursive descent parser framework implemented using template meta-programming techniques. Expression templates [2] allow us to approximate the syntax of Extended Backus Normal Form (EBNF) completely in C. Parser objects are composed through operator overloading and the result is a backtracking, top down parser that is capable of parsing rather ambiguous grammars.
> 
> The Spirit framework enables a target grammar to be written exclusively in C. Inline EBNF grammar specifications can mix freely with other C code and, thanks to the generative power of C templates, are immediately executable.
> 
> Spirit is part of Boost Libraries, a peer-reviewed, open collaborative development effort.

Reference: [Boost.Spirit Home](http://spirit.sourceforge.net/)
