---
layout: post
title: 后端快速搭建网站攻略
categories: 前端
description: 连后端人员都可以拿来做网站的技术。
keywords: Bootstrap,Javascript,UI
---

对于后端人员，最痛苦的莫过于做一套美观兼容的样式，幸好现在网上有很多UI（用户界面）框架，今天就介绍一些简单易学的前端技术。

> 本文最早目的是提供大量简单的前端工具，结果加着加着发现好多学习成本都不低，我会在学习成本高的项目后面加上星号（*）

# 技术选型

## UI

1.  [Bootstrap](http://www.bootcss.com)

    **优点：**

    - 目前使用人数最多的UI库，学习成本相对最低
    - 栅格
    - 响应式布局
    - Bootstrap2完美支持IE 7/8
    - JS库采用jQuery，并且提供轮播图、弹框等组件等

    **缺点：**

    - Bootstrap3不支持IE7/8
    - 用的人太多审美疲劳
    - class命名不够语义化
    - ~~没有逼格~~

2.  [AdminLTE](https://www.almsaeedstudio.com)

    > 一款优秀的基于Bootstrap的模板，集成了许多js库，这个项目就是我基于adminLTE,将部分前端组件替换为更适合国人的组件，并汉化了文档

    **优点：**

    - 有许多优秀插件
    - 继承[Bootstrap](http://www.bootcss.com)
    - 各种结合PHP的框架的二次开发，如果你是个php开发者，使用它连整合的过程都省却了

    **缺点：**

    - 引用大量国外第三方插件

3.  [Foundation](http://foundation.zurb.com/)

    **优点：**

    - 对移动端支持比[Bootstrap](http://www.bootcss.com)好
    - JS库采用[Zepto](http://zeptojs.com/)（这点有好有坏）

    **缺点：**

    - 没有中文文档
    - Foundation4 不支持IE7/8

4.  [Material Design](http://http://materializecss.com/) *

    > Material Design 只是谷歌设计部提供的一种**设计规范**，具体实现UI不下4种，这里贴的是github上找得到项目的

     **优点：**

    - Google 出品，喜欢谷歌风格的可以尝试
    - 相较于千篇一律的Bootstrap UI,ma提供了扁平的谷歌风格

    **缺点：**

    - 没有中文文档

5.  [Ant Design](http://ant.design) *

    **优点：**

    - 蚂蚁金服（支付宝）出品
    - 易于操作复杂事件

    **缺点：**

    - 基于[React](http://facebook.github.io/react/)
    
    > 推荐一款基于ant-design的 企业级后台管理系统 [Antd Admin](https://github.com/zuiidea/antd-admin) 和构建移动端页面的[Ant Design Mobile](https://github.com/ant-design/ant-design-mobile)

6.  [Semantic UI](http://http://www.semantic-ui.cn)

    本来想介绍[Amaze UI](http://amazeui.org/)的，但貌似~~差评太多~~，而且的确没有比上面4个都好的地方，所以介绍[Semantic UI](http://http://www.semantic-ui.cn)

    **优点：**

    - 命名更加语义化（毕竟人家名字就叫语义。。）

    **缺点：**

    - 新兴框架，没有Bootstrap社区活跃
    
7.  [Kendo UI](http://www.kendoui.io/)

    在知乎上看到其他人推荐，所以看了下

    **优点：**

    - 文档／事例有中文镜像，意味着你访问这个网站不用翻墙了（但文档没有中文！！！）
    - 集成了很多jQuery的组件
    - 提供上门培训
    
    **缺点：**
        
    - **收费**
   
	> 个人感觉很适合那种有钱，很传统的公司。。。
	
8.  [DWZ](http://jui.org/)

    一款像ERP界面一样的客户端框架，功能很齐全，如果你是要做**政府／事业单位**的网站，我觉得它的风格很符合

    **优／缺点：**

    - 尽管也是基于bootstrap开发的，但它的样式很像ERP
	

9.  [B-JUI](http://b-jui.com/)

    **优点：**

    - 标签形式显示多个子页面
    - 中文文档
    - 提供了与java/php/.net整合的demo

    **缺点：**
    
    - 不兼容ie6/7
    - 如果不同页面id会遇到麻烦

	> 简单的用了下，文档还是不错的，还提供了些字符串方法，但左侧菜单列表是用json配置的，然后文档还没写，这点要注意下。

10. [Blueprint](http://blueprintjs.com/) *

    **优点：**

    - 适用于复杂、数据密集的页面
    - 移动端支持良好
    - 提供了与java/php/.net整合的demo

    **缺点：**
    
    - 需要Nodejs6以上
    - 基于React
    - 没有中文文档


## 通用类Javascript库

> 虽然部分UI框架也提供了js库，但实际使用中还是会遇到提供的无法满足需求的情况，以下3种都是比较常用的js库

目前主流的通用类Javascript库有：

1. [Jquery](http://jquery.com/),目前使用最多的js库

   >  2.0 版本以后，将不再支持 IE 6/7/8，如果有支持IE的需求，请使用1.11（所以1开头的都支持IE678）

   更多关于jQ的知识请见眼镜猴的js&jQ技术分享

2. [Zepto](http://zeptojs.com/),专注**移动端**的js库,体积不到jQ的一半，也少了很多方法

   > Zepto提供很多方法，并没有放在本体文件里，比如animate，touch，如果需要只需要把对应代码复制到zepto文件中

   [Zepto使用中的一些注意点](http://chaoskeh.com/blog/some-experience-of-using-zepto.html)

3. [Lodash](https://lodash.com/)

   > lodash提供了很多jQ没有的方法，一般Nodejs项目都会引用lodash

## 时间日期类库

使用时间日期类库,一定要设置语言，一般有2种方式,下面以DatePicker为例

从官网下载并加载对应的语言包（简体中文为zh-CN）

```javascript
//在引用的datepicker后面添加下面代码
<script src="//cdn.bootcss.com/pickadate.js/3.5.3/compressed/translations/zh_CN.js" charset="UTF-8"></script>
```

```javascript
//在具体调用datepicker时，添加language:"zh-CN"
 $('#datepicker').datepicker({
   autoclose: true,
   language:"zh-CN"
 });
```

手动设置

```javascript
//在bootstrap-datepicker.js中找到 var dates = $.fn.datepicker.dates ,改为
var dates = $.fn.datepicker.dates = {
   en: {
      days: ["Sunday", "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"],
      daysShort: ["Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
      daysMin: ["Su", "Mo", "Tu", "We", "Th", "Fr", "Sa", "Su"],
      months: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
      monthsShort: ["Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"],
      today: "Today",
      clear: "Clear"
   },
  zh-CN:{
		days: ["星期日", "星期一", "星期二", "星期三", "星期四", "星期五", "星期六", "星期日"],
		daysShort: ["周日", "周一", "周二", "周三", "周四", "周五", "周六", "周日"],
		daysMin:  ["日", "一", "二", "三", "四", "五", "六", "日"],
		months: ["一月", "二月", "三月", "四月", "五月", "六月", "七月", "八月", "九月", "十月", "十一月", "十二月"],
		monthsShort: ["一月", "二月", "三月", "四月", "五月", "六月", "七月", "八月", "九月", "十月", "十一月", "十二月"],
		today: "今日",
		format: "yyyy年mm月dd日",
		weekStart: 1
	}
};
//然后找到var defaults = $.fn.datepicker.defaults 
//将里面的language 改为 'zh-CN'
```

> 使用第二种方式后，具体使用时，不用再添加language参数，因为default中已经设为zh-CN
>

1. [Datepicker](http://jqueryui.com/datepicker/)

   这里需要区分下：jQ提供的是[Datepicker](http://jqueryui.com/datepicker/)，Bootstrap提供的是[bootstartp-datepicker](http://www.bootcss.com/p/bootstrap-datetimepicker/)，我们项目和[adminLTE](https://www.almsaeedstudio.com)用的都是[bootstartp-datepicker](http://www.bootcss.com/p/bootstrap-datetimepicker/)

2. [DateRangePicker](http://www.daterangepicker.com/)

   依然是[Bootstrap](http://www.bootcss.com)推出的，用来选择日期范围（省却了选择时要判断后面的时间不小于前面时间之类的麻烦）

3. [PickaDate](http://amsul.ca/pickadate.js/)

   Github 日期时间类Star最多的项目,可以自定义禁用日期、时间,并且对移动端兼容不错,因为UI风格与adminLTE不符,所以下面的Demo就不引用了,有兴趣的可以去官网看下文档
   
4. [Moment](http://momentjs.cn/)

   日期处理类库,比如格式化／比较／算时间等，有着良好的中文支持，一些时间类组件会依赖它。

5. [Flatpickr](https://chmln.github.io/flatpickr/)

    非常好看的日期选择器！我目前使用的开源的日期选择器里唯一让我感觉每款主题都好看的，而且没有依赖任何插件，**非常推荐**！

## 图表类

> 个人推荐使用echarts,下面的Demo也是采用echarts

1. [Chart](http://www.chartjs.org/)

   adminLTE采用的图表工具，Github上Star最多的图表工具

2. [Echarts](http://echarts.baidu.com/)

   百度推出的图表工具，更适合国人

3. [D3](https://d3js.org/)

   如果你发现一般的竖饼折无法满足你的需求时，可以试试这个
   
4. [Jquery Linechart](https://github.com/kiqs/jquery-linechart)

    基于jQuery的简单图表构建工具，构建出来的很有github的风格。

## 输入框／下拉菜单

1. [Tokenfield](http://sliptree.github.io/bootstrap-tokenfield/)
	
	当你有大量地名／颜色等标签要去多选的时候，可以尝试下Tokenfield——一款基于bootstrap，使用输入框实现标签多选的插件。
	
2. [Selectize](http://selectize.github.io/selectize.js/)

    一款非常优秀的下拉菜单组件，功能比 Tokenfield 更强大。
    
3. [Cleave.js](http://nosir.github.io/cleave.js/)

    规范输入框内容工具，上面的银行卡和手机号验证，对国内不好用。但下面的自定义验证很好用。
	
## 富文本编辑器

> Bootstrap提供的富文本编辑器就是 wysiwyg，但个人更推荐ueditor，Demo中使用的也是ueditor

1. [Wysiwyg](http://www.bootcss.com/p/bootstrap-wysiwyg/)

   一款很轻量的富文本编辑器，只有5KB，但仅支持IE10以上

2. [Ueditor](http://ueditor.baidu.com/)

   百度推出的富文本编辑器，(Mini版已经许久不更新了，而且下载链接已挂)

   [UEditor的最新文档](http://fex.baidu.com/ueditor/)

   > 因为ueditor有很多功能需要与服务器交互，所以最好根据服务端前往官网下载版本，Demo里使用的是完整源码版


## 图片上传

这个得和后台配合。。

1. [FileUploader](http://fineuploader.com/)

   一款Github上Star很多的上传插件，支持移动端,可根据自己的需求定制，Demo里使用的是完整版

   [配置方法](http://docs.fineuploader.com/quickstart/02-setting_options-azure.html)

2. [Image-selecter](https://github.com/shrekshrek/image-selecter)

   一个移动端单图上传工具，主要是修复横竖屏问题，但其他方面不好用

如果传的图片有顺序需求，请使用眼镜猴写的上传后拖拽插件

## 图片

大部分UI框架都提供了轮播图插件，如果无法使用，可以考虑owl.carousel

1. [Owl.carousel](http://owlgraphic.com/owlcarousel/)

   一款pc和移动端都可以使用的轮播图工具
   
   > 如果无法访问，可以尝试 [GithubPreview](http://htmlpreview.github.io/?https://github.com/OwlFonk/OwlCarousel/blob/master/index.html)。另外[Owl.carousel2](http://owlcarousel2.github.io/OwlCarousel2/) 现在是beta版（2016-12-29），有兴趣的可以尝试。关于 1 和 2 有何不同，我也不知道...

2. [BaguetteBox](https://feimosi.github.io/baguetteBox.js/)
    
    一个简单、易用的响应式 Lightbox 图片库。它支持移动端上触滑动手势操作。同时，它还是用纯 JavaScript 编写的。

3. [JqGifPreview](https://github.com/SodhanaLibrary/jqGifPreview)

    一个简单的 jQuery 插件，用于创建 GIF 预览。

4. [JfMagnify](https://github.com/fonstok/jfMagnify)

    基于jQuery，可以为任何 HTML 元素创建放大镜效果（不只是图像）的插件。

5. [Image Blur Plugin](https://msurguy.github.io/background-blur/)

    基于jQuery的图像模糊插件，支持IE6~IE8,但无渐变效果。

6. [Skippr](http://austenpayan.github.io/skippr/)

   基于jQuery的轻量级轮播图插件。我推荐这款的原因就是：Owl.carousel旧版访问不了，新版还是beta。

## 弹框

一开始我是不认为有这个的需求的，因为alert没必要改，bootstrap又提供了不错的modal模板。但下面2款插件我觉得还是要介绍的。

1. [Izimodal](http://izimodal.marcelodolce.com/)

    基于jQuery的优雅、响应式、灵活、轻量级（前面4个是他自称的）弹框插件。

2. [Sweetalert2](https://limonte.github.io/sweetalert2/)

    SweetAlert2 是一个漂亮、可定制的 JS 弹窗插件，它用于替代浏览器默认的弹窗效果。一旦使用了它，基本你就告别alert()/confirm()等原生方法了。
    
## 滚动

1. [FullPage](http://alvarotrigo.com/fullPage/)

   一般官网或产品宣传页可以用这个做全屏滚动
   
2. [Scroll Reveal](https://scrollrevealjs.org/)

    无论是为桌面，或是移动浏览器，ScrollReveal 插件都可以轻松、快速的帮助你为其创建页面滚动显示动画。

## 表格

大部分UI框架都提供了静态分页按钮，配合服务端渲染时循环，可以实现后台分页

如果想实现前台分页，可以选择下面的插件

1. [DataTables](https://www.datatables.net/)

   基于jQ的表格插件（自带分页），支持前台分页，目前Java项目正在使用
   
2. [Tabulator](http://olifolkerd.github.io/tabulator/)

    基于jQ的表格插件，做出来的表格画风很像Chrome的控制台。

## 地图

1. [百度地图](http://lbsyun.baidu.com/)

2. [高德地图](http://developer.amap.com/)
   阿里旗下

   ​

## 下拉菜单／树

所有的UI框架都提供下拉菜单（dropdown）

> Dropdown一般用来做菜单而不是选择

如果上面都满足不了需求，请使用下面的树插件

1. [jsTree](https://www.jstree.com/)

   一个基于jQ的树插件，Github上Star最多

## 模板 

1. [artTemplate](https://github.com/aui/artTemplate)

   新一代 javascript 模板引擎（Nodejs也可以使用）


## 图标

大部分UI框架都提供了一定数量的图标，但如果感觉UI库提供的图表不够，可以上这里找找

1. [iconfont](http://www.iconfont.cn/)

   阿里的图表库，只要引用一个css，就可以定制图标

## 网站统计

统计网站的流量， 用户群体等等

1. [百度统计](http://tongji.baidu.com/)

2. [Google Analytics](http://www.google.com/intl/zh-CN/analytics/)

   国内不推荐。。。
   
## 博客搭建工具
> 具体的选型请参考知乎上的这篇文章 [FarBox、Jekyll、Octopress、ghost、marboo、Hexo、Medium、Logdown、prose.io，这些博客程序有什么特点](https://www.zhihu.com/question/21981094)，这里列出2个笔者觉得比较好的工具。

1. [Jekyll](https://github.com/jekyll/jekyll)   

	只需几秒钟就能跑起一个静态网站（支持markdown语法，赞！），可以部署在github上。
	
2. [FarBox](https://www.farbox.com/)

	引用一段知乎的回答好了
	> 国产，对中文支持好。类似于国外的 Scriptogr.am 和 Calepin（类似还有很多，但这两个是主流，calepin 是 dropbox 用作博客的始祖），利用 dropbox 做仓库储存文章，Markdown 写作。一键安装，不需要懂技术，使用门槛低。可以生成静态网站（这点类似 site44）和博客。作为个人博客是个不错的选择，不用管数据库什么的，专注写作。
	
## 特效(duang~)

推荐一个前端特效展示地 [CodePen](http://codepen.io/)

> 以前网上看到过很多很有意思的动画效果，一直没有收藏起来，之后我看到的话，都会陆续收录到下面

1. [particles.js](http://vincentgarreau.com/particles.js/)

	一款基于html5 canvas的轻量级炫酷js粒子动画库插件。
	
2. [动画视差效果](http://codepen.io/anatravas/pen/NbggmR)
	
	使用 jQuery 插件创建视差效果，并用 CSS 动画制作的闪烁与流星。
	
3. [日出日落动画](http://codepen.io/davidkpiano/pen/VmMWZW)	

	纯 CSS 还原 Dribbble 上 Denys Boldyriev 和 Andrey Pixy 所设计的日出/日落动画效果，目前只能在 Chrome 浏览器中运行。
	
4. [Css Loader](http://codepen.io/CKH4/pen/ZGNyep/)

    这是一个利用 Slim+CSS 预处理器 Stylus 实现的简单动画。作者写代码很精炼、简洁。
   
5. [Rainbow Loader](http://codepen.io/jackrugile/pen/JddmaX/)

    为客户端改良的纯 CSS 实现的彩虹加载动画。
    
6. [Light Loader](http://codepen.io/jackrugile/pen/BlDjk/)

    CSS+JS 实现的艳丽火花效果的 Canvas 加载动画。

7. [CSS Stairs Loader](http://codepen.io/ispal/pen/mVaaJe/)

    纯 CSS 实现的楼梯循环加载动画。
    
8. [ChoreographerJS](https://christinecha.github.io/choreographer-js/)

    用于处理复杂动画的简单库。

## TODO:

- [ ] 使用 Ant Design Mobile
- [ ] 将一些其他框架好的组件更新到这个项目里 