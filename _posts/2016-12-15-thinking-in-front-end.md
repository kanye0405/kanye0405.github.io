---
layout: post
title: 关于《资深Web技术专家曹刘阳：2016年前端技术观察》的一些想法
categories: 前端
description: 知乎前端圈年末撕逼大戏，如何评价真阿当的文章：《2016年前端技术观察》？
keywords: JavaScript, Nodejs, React
---

知乎前端圈年末撕逼大戏，[如何评价真阿当的文章：《2016年前端技术观察》](https://www.zhihu.com/question/53625757)？

每年年底都有大神总结今年前端发展如何，有哪些不错的技术云云，但今年的 [资深Web技术专家曹刘阳：2016年前端技术观察](http://geek.csdn.net/news/detail/128912) 这篇文章算是不按套路出牌了，把TS、CoffeeScript、ES6、Angular、React、CSS预处理器、Node.js……都批判了一番，作为一条咸鱼，我也发表下自己的看法。

## 前言

我一直认为技术是为业务服务的，所以我认为技术只要能**快速解决问题**就可以了，所以当一个新技术出现的时候，我更加关注的是：

    1. 他解决了什么问题。

    2. 他上手速度、开发速度、维护难易度是否超过了同类型的前辈。

所以我下面的讨论都会围绕上面提到的2点来谈。

## CSS预处理器

我只用过less和postCss，所以我也就只谈这2个吧。首先说下观点：我不认同阿当老师说的CSS预处理器"性价比不高"。

less/postCss 的学习成本极低，任何一个会css的花不了一个下午就能用起来less，阿当老师提到的"安装预处理工具"其实只是装一个gulp/grunt/fis3而已。我前面的半天已经把学习使用这些脚手架的时间算进去了。

所以阿当老师说的学习门槛是不成立的，而与之对应的却是丰厚的好处：

    1.我们可以写出逻辑更清晰的样式,可能只有维护过一个1000+行的css后才会明白这种结构多么难能可贵
    
    ```css
    .module {
    　.action {
    　　a, a:hover {
    　　　//styles
    　　}
    　}
    }
    ```
    
    2.可以方便地屏蔽浏览器私有语法差异，以前要写个box-shadow很痛苦，因为每个浏览器都有自己的叫法
    
    ```css
    .shadow {
        box-shadow:-1px -1px 5px #666,-1px -1px 5px #666,1px 1px 5px #666,1px 1px 5px #666;
        -moz-box-shadow:-1px -1px 5px #666,-1px -1px 5px #666,1px 1px 5px #666,1px 1px 5px #666;
        -webkit-box-shadow:-1px -1px 5px #666,-1px -1px 5px #666,1px 1px 5px #666,1px 1px 5px #666;
        filter: progid:DXImageTransform.Microsoft.Shadow(Strength=5, Direction=0, Color='#666666')
        progid:DXImageTransform.Microsoft.Shadow(Strength=5, Direction=90, Color='#666666')
        progid:DXImageTransform.Microsoft.Shadow(Strength=5, Direction=180, Color='#666666')
        progid:DXImageTransform.Microsoft.Shadow(Strength=5, Direction=270, Color='#666666');/*for ie 7,8*/
    }
    ```
    
    上面的例子看着好像很多，但其实对于不同浏览器需要执行的只有一行
    
    3.可以轻松实现多重继承。概念有点类似于java的类，不过这个我不怎么使用，所以就不赘述了。
    
    4.除此之外 postCss的autoprefix，可以给css加上 if 判断，再也不用很蠢得在js去做逻辑判断再修改样式了。

## ES6等新语法

讲个笑话，代码界的2个极端，Python和JavaScript。前者Python 3 发布已经 8 年了，Python 社区却依然在使用 Python 2.7。而后者正好相反，把还没有实现的语言特性都用到生成环境中了！

我感觉现在的前端仿佛是代码界的大跃进，Github Trending里前端项目占一半，天天有新语法、新轮子出现，当然哪些是kpi项目就不得而知了。我最为半个前端很痛苦，导致我痛苦的就是我日益增长的眼界和落后的实际项目使用技术之间的矛盾。现在和人聊天不敢说我我还在用bootstrap+jq，不敢说es2015用不惯，因为这太low了。

## Angular/React/Vue等前端框架

首先要肯定的是它们都大大缩减了开发的时间，个人感觉学习成本是Angular > React > Vue。曾经使用过基于react的ant-design，涉及的知识从虽然做出来页面很简洁，但学习成本太高，要想熟练的使用，你需要至少熟练es6、react、webpack，最好再把antd-tool、dva之类用起来。如果现在有个管理界面要搭，技术选型我一定选bjui而不是antd-admin。

## Node

我认为Node主要作用并不是连接数据库替代服务器，而是做中间件。即让前端人员像客户端一样调服务端人员的接口，而不是去改一张张jsp/php/vm文件。

## 全栈

不知道什么时候起，这个词变成贬义词了，仿佛只要是全栈就是那种学了点js到处吹的人。我身边很多人都认为语言应该重深度而非广度。什么是深度和广度呢？

> 假如你是一个Java码农，你在会ssm框架基础上，下一个要学的是缓存还是用jq+bootstrap做页面？

* 选择缓存，目标是提升网站的访问量上限，属于增加你在java上的深度。
* 选择学前端，就能当团队缺少前端时，去分担前端的任务，属于增加你的广度。

我的选择类似于 T 字形，在java上浅尝而止，像docker、spark这类目前我都不打算接触。我会把学习这些的时间拿来看前端、数据库、服务器。为什么一个javaer要看前端？

    1.更好的对接项目，如果不去想前端怎么实现，你就很难完整的给出前端需要的数据，然后开发的时候一会加个字段，一会改个格式的。
    2.除非是大公司，身兼多职在所难免。
    3.语言是相通的，即使对于后端来说最难的css在不考虑兼容低版本IE、响应式布局情况下入门也是很快的。

所以我认为的全栈就是某方面强，然后对于相邻环节并非一窍不通。比如前端要知道设计为何这么做交互，后端怎么存数据的；设计要知道产品是怎么把运营提出的需求归纳为开发的需求的，开发人员在实现这个交互的时候会不会很花时间。

## 杂谈

感觉现在开发一款app/网站的成本真是太低了，国内百家争鸣的云平台、github大量项目/插件源码，个人感觉现在开发一款app成本应该只有原来的20%。

## 最后贴上一些大牛的看法

* [如何评价真阿当的文章：《2016年前端技术观察》？ - 大漠的回答 - 知乎](https://www.zhihu.com/question/53625757/answer/135883671)
* [如何评价真阿当的文章：《2016年前端技术观察》？ - 贺师俊的回答 - 知乎](https://www.zhihu.com/question/53625757/answer/135867453)
