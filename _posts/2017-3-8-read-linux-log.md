---
layout: post
title: 如何在linux下看java日志
categories: Java
description: linux下看java日志
keywords: Linux, Java， Log
---

在Java开发中，难免在线上遇到bug，这时如何利用日志快速定位问题就很关键了，最早我只会傻傻的使用`tail -200f xxx.log` 但有很多不方便的地方：

* 无法准确定位bug，得一行一行翻

* 如果线上日志量大，要翻很久才能翻到

最近学会了一种新的方法  `cat xxx.log |grep -A 10 "ERROR"` 

这段的意思是 搜索xxx.log中 ERROR部分，并把其后10行打印出来。同理，ERROR这个关键词可以换成其他能更精确定位到bug的关键词。


