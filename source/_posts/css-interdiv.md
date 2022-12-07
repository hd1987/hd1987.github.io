---
title: css控制 外层div高度未知 内层div高度100%
date: 2016-03-24 08:39:17
categories:
  - Note
tags:
  - css
---

外层：div设置超出不显示，
内层：div底部内边距10000px，div底部外边距-10000px。

``` css
.outerDiv { overflow:hidden;}
.interDiv { padding-bottom:10000px; margin-bottom:-10000px;}
```