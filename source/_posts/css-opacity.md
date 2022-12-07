---
title: css透明度设置opacity
date: 2016-03-24 08:31:36
categories:
  - Note
tags:
  - css
---

``` css
.opacity{
  filter:alpha(opacity=50);   /* IE */
  opacity:0.5;                /* 支持opacity的浏览器*/
  -moz-opacity:0.5;           /* 老版Mozilla */
  -khtml-opacity:0.5;         /* 老版Safari */
}
```
