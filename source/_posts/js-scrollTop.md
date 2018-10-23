---
title: div移动到顶部固定不变
date: 2016-03-25 23:15:06
tags: js
---

``` js
//获取要定位元素距离浏览器顶部的距离
var navH = $(".hb").offset().top;
//滚动条事件
$(window).scroll(function(){
//获取滚动条的滑动距离
var scroH = $(this).scrollTop();
//滚动条的滑动距离大于等于定位元素距离浏览器顶部的距离，就固定，反之就不固定
if(scroH>=navH){
	$(".hb").css({"position":"fixed","top":0});
	}else if(scroH<navH){
	$(".hb").css({"position":"static"});
	}
})
```