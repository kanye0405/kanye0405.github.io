---
layout: post
title: Arrays.asList()使用注意事项
categories: Java
description: 关于Arrays.asList()使用注意事项
keywords: Java
---

今天发现个异常，java.lang.UnsupportedOperationException

通过网上一番查找，发现原因是采用Arrays.asList()新建list，不能调用add或remove方法。

具体原因是arrays.aslist中，返回的不是原来的传统意义上的java.util.arraylist了，
而是自己工具类的一个静态私有内部类，并没有提供add和remove方法。

所以如果要生成长度可变的ArrayList，还是老老实实new一个吧，不要用Arrays.asList()。
