---
id: 376
title: Lisp和Objective-C原来是亲戚
date: 2011-07-07T15:35:24+00:00
author: Shu
layout: post
guid: https://www.wavether.com/?p=376
permalink: /376
aktt_notify_twitter:
  - yes
aktt_tweeted:
  - 1
categories:
  - 中文
  - Computer
  - Mac
  - Programming
tags:
  - lisp
  - objective-c
  - programming
  - smalltalk
---
今天洗澡的时候——这通常是我灵感显现之时——忽然发现Lisp和Objective-C的语法有相似之处。且看：

> `[NSString doubleValue]`

这是Objective-C调用类NSString的方法doubleValue；还有

> `(* 3 4)`

这是Lisp调用乘法计算3和4的积。

查了一下Wikipedia，原来经典[Lisp](http://en.wikipedia.org/wiki/Lisp_(programming_language))作为老牌程式编程语言，影响了作为面向对象鼻祖的[SmallTalk](http://en.wikipedia.org/wiki/Smalltalk)的设计，SmallTalk又影响了[Objective-C](http://en.wikipedia.org/wiki/Objective-C)的设计以及现代版[Common Lisp](http://en.wikipedia.org/wiki/Common_Lisp)的设计，特别是两者面向对象的部分。

> Lisp deeply influenced Alan Kay, the leader of the research on Smalltalk, and then in turn Lisp was influenced by Smalltalk, by adopting object-oriented programming features (classes, instances, etc.) in the late 1970s.

摘自 http://en.wikipedia.org/wiki/Lisp\_(programming\_language)#Language_innovations

> The syntax and runtime behaviour of the Objective-C programming language is strongly influenced by Smalltalk.

摘自 http://en.wikipedia.org/wiki/Smalltalk#Influences

巧合的是我很多年没有学习新的编程语言了，最近却阴差阳错同时开始学Lisp和Objective-C。两者的起因都是因为换了Macbook。前者是由于没能成功编译Kscope而重新检视用vim和Emacs来浏览代码，看了Emacs-Lisp，以及这本关于Lisp的书——[Practical Common Lisp](http://www.gigamonkeys.com/book/)；后者则是凑个热闹，看看Cocoa比多年前Windows上做开发的MFC进化了多少。

刚开了个头，还是很有趣的。
