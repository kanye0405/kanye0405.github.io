---
layout: post
title: 最近使用前端插件时遇到的问题
categories: Javascript
description: 一些后台页面使用插件时踩过的坑
keywords: Admin,Javascript,plugins
---

最近做了几个后台页面，用到了datetimepicker、daterangerpicker、distpicker、select2、thenjs、wangEditor，其中某些插件用起来遇到些问题。

## thenjs无法调到下个异步方法

例子没看仔细，每个方法执行结束时,需要调cont()方法。

## AdminLTE 对select2订制的样式无效

AdminLTE对select2的选择框，做了美化，然而我在实际实用时发现这些样式全被覆盖了。
原因是AdminLTE.css 和 select2.css命名一样，所以哦权限也一样，只需要把select2.css放在AdminLTE.css上面就能解决了

## daterangepicker 加了`timePicker24Hour:true`后时间无法选择24小时

目前bootstrap下的时间插件，对于时间定义不一样 hh在datetimepicker中表示24小时制，而在daterangepicker中只表示12小时（分钟也不同，一个mm一个ii），
这就导致daterangepicker中时间选择不了大于12的数字。

解决方法就是把format中的hh改为HH

## select2无法初始化多选

根据官网的例子，` $exampleMulti.val(["CA", "AL"]).trigger("change");` 这么写即可

暂时这么多，之后更能会总结下支付宝和微信对接时遇到的坑，先吐槽下：微信公众号支付对接真难