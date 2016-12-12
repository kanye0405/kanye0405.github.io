---
layout: page
title: About
description: 会一点代码的咸鱼
keywords: Zhenyu L, 李振羽
comments: true
menu: 关于
permalink: /about/
---

一只会一点代码的咸鱼

## 坚信

* 熟能生巧
* 努力改变人生

## 联系

* GitHub：[@kanye0405](https://github.com/mzlogin)
* 博客：[{{ site.title }}]({{ site.url }})
* 知乎: [@李振羽](https://www.zhihu.com/people/li-zhen-yu-52-84/activities)


## Skill Keywords

#### Java Developer Keywords
<div class="btn-inline">
    {% for keyword in site.skill_java_keywords %}
    <button class="btn btn-outline" type="button">{{ keyword }}</button>
    {% endfor %}
</div>

#### Front End Developer Keywords
<div class="btn-inline">
    {% for keyword in site.skill_front_end_keywords %}
    <button class="btn btn-outline" type="button">{{ keyword }}</button>
    {% endfor %}
</div>

#### Datebase Developer Keywords
<div class="btn-inline">
    {% for keyword in site.skill_datebase_keywords %}
    <button class="btn btn-outline" type="button">{{ keyword }}</button>
    {% endfor %}
</div>
