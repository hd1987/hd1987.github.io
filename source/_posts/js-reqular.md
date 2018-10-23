---
title: js正则表达式限制文本框只能输入数字,小数点,英文字母 
date: 2016-03-25 23:29:18
tags: js
---

1.文本框只能输入数字代码(小数点也不能输入)
``` html
<input onkeyup="this.value=this.value.replace(/\D/g,'')" onafterpaste="this.value=this.value.replace(/\D/g,'')">
```
2.只能输入数字,能输小数点.
``` html
<input onkeyup="if(isNaN(value))execCommand('undo')" onafterpaste="if(isNaN(value))execCommand('undo')">
<input name=txt1 onchange="if(/\D/.test(this.value)){alert('只能输入数字');this.value='';}">
```
3.数字和小数点方法二
``` html
<input type=text t_value="" o_value="" onkeypress="if(!this.value.match(/^[\+\-]?\d*?\.?\d*?$/))this.value=this.t_value;else this.t_value=this.value;if(this.value.match(/^(?:[\+\-]?\d+(?:\.\d+)?)?$/))this.o_value=this.value" onkeyup="if(!this.value.match(/^[\+\-]?\d*?\.?\d*?$/))this.value=this.t_value;else this.t_value=this.value;if(this.value.match(/^(?:[\+\-]?\d+(?:\.\d+)?)?$/))this.o_value=this.value" onblur="if(!this.value.match(/^(?:[\+\-]?\d+(?:\.\d+)?|\.\d*?)?$/))this.value=this.o_value;else{if(this.value.match(/^\.\d+$/))this.value=0+this.value;if(this.value.match(/^\.$/))this.value=0;this.o_value=this.value}">
```

<!--more-->

4.只能输入字母和汉字
``` html
<input onkeyup="value=value.replace(/[\d]/g,'') "onbeforepaste="clipboardData.setData('text',clipboardData.getData('text').replace(/[\d]/g,''))" maxlength=10 name="Numbers">
```
5.只能输入英文字母和数字,不能输入中文
``` html
<input onkeyup="value=value.replace(/[^\w\.\/]/ig,'')">
```
6.只能输入数字和英文
``` html
<input onKeyUp="value=value.replace(/[^\d|chun]/g,'')">
```
7.小数点后只能有最多两位(数字,中文都可输入),不能输入字母和运算符号:
``` html
<input onKeyPress="if((event.keyCode<48 || event.keyCode>57) && event.keyCode!=46 || /\.\d\d$/.test(value))event.returnValue=false">
```
8.小数点后只能有最多两位(数字,字母,中文都可输入),可以输入运算符号:
``` html
<input onkeyup="this.value=this.value.replace(/^(\-)*(\d+)\.(\d\d).*$/,'$1$2.$3')">
```
9.只能输入汉字：
``` html
<input onkeyup="value=value.replace(/[^\u4E00-\u9FA5]/g,'')" onbeforepaste="clipboardData.setData('text',clipboardData.getData('text').replace(/[^\u4E00-\u9FA5]/g,''))">
```
10.只能输入数字：
``` html
<input onkeyup="value=value.replace(/[^\d]/g,'') "onbeforepaste="clipboardData.setData('text',clipboardData.getData('text').replace(/[^\d]/g,''))">
```
11.只能输入英文和数字：
``` html
<input onkeyup="value=value.replace(/[\W]/g,'') "onbeforepaste="clipboardData.setData('text',clipboardData.getData('text').replace(/[^\d]/g,''))">
```
12.控制输入框只能输入文字或数字，也可以不允许输入特殊字符
这里不允许输入如下字符: (像 !@#$%^&* 等)
``` html
<textarea rows=2 cols=20 name=comments onKeypress="if ((event.keyCode > 32 && event.keyCode < 48) || (event.keyCode > 57 && event.keyCode < 65) || (event.keyCode > 90 && event.keyCode < 97)) event.returnValue = false;">
```
13.只禁止空格输入
``` html
onkeyup="value=value.replace(/\s/g,'')"
```
14.只能输入中文和英文：
``` html
onkeyup="value=value.replace(/[^\a-zA-Z\u4E00-\u9FA5]/g,'')" onbeforepaste="clipboardData.setData('text',clipboardData.getData('text').replace(/[^\a-zA-Z\u4E00-\u9FA5]/g,''))"
```