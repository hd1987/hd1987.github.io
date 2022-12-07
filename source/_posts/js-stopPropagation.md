---
title: Query中阻止事件冒泡方式  
date: 2016-03-25 23:50:53
categories:
  - Note
tags:
	- js
---

``` js
//event.stopPropagation();
$("#div1").mousedown(function(event){
	event.stopPropagation();
})
```