---
layout: post
title: Dubbo使用感受及遇到问题总结
categories: Java
description: 第一次将体验了完整了项目拆成多个项目，就把遇到的问题都总结在这里吧
keywords: Dubbo, Java
---
一晃将近2个月没更新博客，其实是因为之前忙于将公司主业务拆成两个项目（恩，可以理解为分布式吧），这个过程中我是被maven和dubbo弄的欲仙欲死，低级的、高级的错误都犯了，现在总结一下吧。

> [Dubbo](http://dubbo.io/)是阿里推出的开源分布式服务框架， 

# 遇到的问题 

## 无法通过dubbo调到Provider的方法

在查看dubbo官网用户说明时有这样的一段话：

> **注意：只有group，interface，version是服务的匹配条件，三者决定是不是同一个服务，其它配置项均为调优和治理参数。**

所以一定要检查provider和consumer的 group 和 version，我就是因为2个项目的group导致调不到方法。

## 一定概率调不到Provider接口

经询问我司老司机得知，如果多个provider的group，interface，version相同，当consumer调这个方法的时候就会被负载均衡到另一个方法，所以只需将这组方法的group或version与旧方法区分开就可以了。

> 另外，个人认为version是用来区分不可兼容的版本差别的，group是区分开发时不同小组，防止混用的。所以开发时最好不要只用一个version来做区分。

## 部署后的项目仍然调旧接口

这个坑涉及到maven的一个使用陋习了，我们有的时候修改了项目后打包时感觉修改的内容太少，不会升级版本号，于是dubbo就扔调旧的接口了。遇到这种情况只要升级下版本号就好了。

## 一调接口就报"消息发送失败"错误

切记！切记！dubbo中使用的model一定是序列化。

## 项目基于maven互相调用，deploy失败

dubbo项目切忌a调b，b又调a这样循环调用会导致maven打包失败。尤其不要因为偷懒在自己的接口调用别人的model。这样别人调你的接口时，又要调另一个人。
如果一定要调，可在pom文件里添加 <exclusions> 来排除依赖。




