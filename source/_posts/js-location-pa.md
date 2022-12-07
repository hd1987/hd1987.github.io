---
title: jquery判断地址栏是否存在某参数 
date: 2016-03-25 23:19:35
categories:
  - Note
tags:
	- js
---

``` js
var arr = new Array();
var pa;
r = window.location.search;//获取地址栏问号之后的参数（包括问号）
r = r.substr(1);//去除问号
arr = r.split('&');//切割多个参数为数组
for(i=0;i<arr.length;i++){
	pa = arr[i].split('=');//把单个参数的名称和值拆分开
	if(pa[0]=='b' && pa[1]=='bbb'){//判断参数名称和值是否对应
		console.log('abcdefg');//输出
	}
}
```