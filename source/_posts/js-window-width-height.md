---
title: Javascript、Jquery获取浏览器和屏幕各种高度宽度
date: 2016-10-31 13:44:11
categories:
  - Note
tags:
  - js
---

Javascript:

```js
document.body.clientWidth        //网页可见区域宽(body)
document.body.clientHeight       //网页可见区域高(body)
document.body.offsetWidth        //网页可见区域宽(body)，包括border、margin等
document.body.offsetHeight       //网页可见区域宽(body)，包括border、margin等
document.body.scrollWidth        //网页正文全文宽，包括有滚动条时的未见区域
document.body.scrollHeight       //网页正文全文高，包括有滚动条时的未见区域
document.body.scrollTop          //网页被卷去的Top(滚动条)
document.body.scrollLeft         //网页被卷去的Left(滚动条)
window.screenTop                 //浏览器距离Top
window.screenLeft                //浏览器距离Left
window.screen.height             //屏幕分辨率的高
window.screen.width              //屏幕分辨率的宽
window.screen.availHeight        //屏幕可用工作区的高
window.screen.availWidth         //屏幕可用工作区的宽
```

Jquery:

```js
$(window).height()                 //浏览器当前窗口可视区域高度
$(document).height()               //浏览器当前窗口文档的高度
$(document.body).height()          //浏览器当前窗口文档body的高度
$(document.body).outerHeight(true) //浏览器当前窗口文档body的总高度 包括border padding margin
$(window).width()                  //浏览器当前窗口可视区域宽度
$(document).width()                //浏览器当前窗口文档对象宽度
$(document.body).width()           //浏览器当前窗口文档body的宽度
$(document.body).outerWidth(true)  //浏览器当前窗口文档body的总宽度 包括border padding margin
```


