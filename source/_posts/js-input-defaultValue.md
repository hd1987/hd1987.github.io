---
title: input默认提示文字
date: 2016-03-25 23:16:32
tags: js
---

``` js
//input默认提示文字
$('.input_text_val').bind({ 
focus:function(){ 
	if (this.value == this.defaultValue){ 
		this.value="";
	} 
}, 
blur:function(){ 
	if (this.value == ""){ 
		this.value = this.defaultValue; 
	} 
} 
})
```