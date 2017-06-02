---
layout: post
title: Mac下Maven在新的终端窗口下不生效解决方法
categories: Java
description: maven在OhMyZsh环境下，在新的终端中无效
keywords: Maven,Mac
---

最近重新装了Maven，本来一切步骤顺利。 输入`mvn -v`指令也有回应。可当我打开Intellij Idea时，发现`mvn -v`失效了。
重启了电脑后，发现在终端里`mvn -v`也失效了，执行了`source ~/.bash_profile`命令后又好了。但我总不能没打开一个终端就`source ~/.bash_profile`一遍啊。
折腾了好久，终于看到网上一篇文章讲，是因为OhMyZsh的环境变量是存在~/.zshrc里的。

于是只需要把在~/.bash_profile配置的环境变量复制到~/.zshrc，再`source ~/.zshrc`就可以了。