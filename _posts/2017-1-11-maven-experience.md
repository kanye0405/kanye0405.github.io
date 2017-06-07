---
layout: post
title: Maven使用感受及遇到问题总结
categories: Java
description: 总结maven使用时出过的一些低级错误
keywords: Maven,Java
---

新年第一篇文章，[多说](http://duoshuo.com/)和[百度统计](http://tongji.baidu.com/)终于加上了，希望大家多多评论。另外总结mac上推荐工具的还在草稿区，争取年前写完。

> 关于Maven的介绍及使用方法这里就不赘述了，下面列一些不错的文章。

[Maven3实战笔记01环境配置与使用入门](http://suhuanzheng7784877.iteye.com/blog/1066917)

# 遇到的问题

> 目前只总结这些问题，我会随着开发时遇到/解决新的问题更新这篇文章。

## 本地无法打包

我使用的是 Intellij Idea ，在执行`mvn clean package deploy -Dmaven.test.skip`时，会遇到报错信息

检查后发现，如果项目存在无法运行的代码，就无法打包，进而无法发布到私人仓库。

## 打包上传等显示一切成功，在私人仓库却没找到

一个比较低级的错误,我打的是Snapshot包，我们公司snapshot默认不显示，必须点 Show All Versions 才能看到，于是我白花了2个小时...

## 远程仓库已经有新版本，本地没有更新

如果新版本的版本号高于当前使用的版本号，只需要 点击 Intellij Idea 右边的Maven Projects 里的 重新导入 按钮（2个箭头循环的样子）。

如果不用IDE，也可以使用maven自带的命令`mvn clean install`安装pom上的jar包

> -e 代表打印日志，如果报错可以通过-e查看详细错误信息

如果新版本的版本号与当前使用的相同（开发时，其他人只改了一点不想更新版本），只需要删除.m2下本地对应jar包，然后通过上面的方法重新导入。

## install时候报 Could not find artifact xxx in nexus

昨天install时候报了个很奇怪的错误，报错信息如下：

```
Failed to execute goal on project biz: Could not resolve dependencies for project xxx: Failed to collect dependencies at com.xxx: Failed to read artifact descriptor for xxx: Could not find artifact xxx in nexus (http://115.159.71.249:9091/content/groups/public/) -> [Help 1]
org.apache.maven.lifecycle.LifecycleExecutionException: Failed to execute goal on project biz: Could not resolve dependencies for project xxx: Failed to collect dependencies at xxx

```

去网上找也没什么匹配的答案，后来和同事琢磨出原因了。我们项目并没有用到这个包（用的是他这个项目的其他Module），所以这部分代码没有传到私人仓库中。但引用时却引用到了。

解决方法：只要把这个jar deploy就可以了。

## mvn install后 IDE仍无法提示修改的内容

应该是IDE本地的缓存导致的，重启IDE或者把pom里对应的依赖先删掉，再加上就好了
