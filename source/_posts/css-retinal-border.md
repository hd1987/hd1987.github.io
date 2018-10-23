---
title: Retina屏幕下border 1px解决方案
date: 2016-10-04 00:43:20
tags: [css, retina]
---

retinal屏幕下@2x, @3x会使css设定好的border 1px变成2倍或者3倍。
以@2x为例，用css解决这个放大的问题（此方法能解决直线）

```css
.scale{
  position: relative;
}
.scale:after{
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  border-bottom: 1px solid #ddd;
  -webkit-transform: scaleY(.5);
  -webkit-transform-origin: 0 0;
}
```


