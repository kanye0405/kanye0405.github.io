---
layout: post
title: Findbugs使用心得
categories: Java
description: findbugs Intellij Idea下安装使用方法
keywords: Java,Bug,Intellij Idea
---

最近闲来无事，讲讲findbugs吧。


# Findbugs 是什么


> Findbugs是一个静态分析工具，它检查类或者JAR 文件，将字节码与一组缺陷模式进行对比以发现可能的问题。
Findbugs自带检测器，其中有60余种Bad practice，80余种Correctness，1种 Internationalization，
12种Malicious code vulnerability，27种Multithreaded correctness，23种Performance，43种Dodgy。
我们还可以自己配置检查规则(做哪些检查,不做哪些检查)，也可以自己来实现独有的校验规则(用户自定义特定的bug
模式需要继承它的接口,编写自己的校验类,属于高级技巧)。


  简而言之，他是一种检查你的java代码中有哪些bug的工具（当然业务逻辑的bug他就无能为力了）。


# 使用Intellij Idea 安装

  首先打开Preferences,Mac下默认快捷键是 `Command + ,`, 然后选择Plugins（插件）
  
  这里列出的插件都是你本地已经有的，Intellij Idea会帮你安装一些插件。然后选择下面的Browse Respositories按钮。
  
  ![安装Findbugs-1](/images/posts/java/findbugs-install-1.png)
  
  输入findbugs，就会搜索到数条插件。选择第二条，点击Install，就可以安装到本地了
  
  ![安装Findbugs-1](/images/posts/java/findbugs-install-2.png)
  
  
# 如何检查项目

  右键单击项目，选择Findbugs，选择Analyze Project Files(如果只想扫描一个文件就右键单击那个文件，选择Analyze Selected File)
  
  ![使用Findbugs-1](/images/posts/java/findbugs-install-3.png)
  
  执行完成，可以看到bugs被分成不同类型排列下来。
  
  ![使用Findbugs-2](/images/posts/java/findbugs-install-4.png)


# 解决问题

  首先选择一个错误

  ![修改findbugs提出bug1](/images/posts/java/findbugs-use-1.png)
  
  可以看到右面提供了大量错误的描述信息，意思是可能能让别人通过这个方法修改里面的内容。
  所以我们只要返回不能被修改的方法就行了，比如clone对象。


  当然有的同学英语英语水平比较差，看不懂解释怎么办？只需要拿错误信息标题去网上搜索，就能
  获得翻译好的bug描述及解决方法，比如刚才这个问题，只需要搜索 May expose internal representation
  就能发现很多博客已经翻译了错误描述及解决方法。
