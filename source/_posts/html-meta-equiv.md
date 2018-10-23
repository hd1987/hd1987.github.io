---
title: Meta告知IE浏览器兼容模式
date: 2016-03-23 12:42:04
tags: [html, meta]
---

x-ua-compatible(浏览器兼容模式)
仅对IE8+以效
告诉浏览器以什么版本的IE的兼容模式来显示网页

``` html
<meta http-equiv="X-UA-Compatible" content="IE=5" >
<meta http-equiv="X-UA-Compatible" content="IE=7" >
<meta http-equiv="X-UA-Compatible" content="IE=8" >
<meta http-equiv="X-UA-Compatible" content="IE=edge" >
```

其中最后一行IE=edge是永远以最新的IE版本模式来显示网页的。
另外加上Emulate模式

``` html
<meta http-equiv="X-UA-Compatible" content="IE=EmulateIE7" >
<meta http-equiv="X-UA-Compatible" content="IE=EmulateIE8" >
```

Emulate模式后则更重视<!DOCTYPE>
(细心的人会注意到，用IE9去访问带有x-ua-compatible的页面时是不会出现兼容视图按钮的)

``` html
<meta http-equiv="X-UA-Compatible" content="IE=EmulateIE8" />
```
