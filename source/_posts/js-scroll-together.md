---
title: 两个div同步滑动（js, jquery）
date: 2016-03-25 23:08:45
categories:
  - Note
tags:
	- js
---

方法一.使用js（适用web和wap）
``` html
//横向滚动条同步
<div id="div1" style="width:500px; overflow:scroll;"  onscroll="document.getElementById('div2').scrollLeft = this.scrollLeft;">
	<div style="width:800px; height:50px;"></div>
</div>
<div id="div2" style="width:500px; overflow:scroll;"  onscroll="document.getElementById('div1').scrollLeft = this.scrollLeft;">
	<div style="width:800px; height:50px;"></div>
</div>

//竖向滚动条同步
<div id="div1" style="width:500px; overflow:scroll;"  onscroll="document.getElementById('div2').scrollTop = this.scrollTop;">
	<div style="width:800px; height:50px;"></div>
</div>
<div id="div2" style="width:500px; overflow:scroll;"  onscroll="document.getElementById('div1').scrollTop = this.scrollTop;">
	<div style="width:800px; height:50px;"></div>
</div>
```

<!--more-->

方法二.使用jquery（仅适用web）
``` js
$('#sourceDiv').scroll( function() { 
	$('#targetDiv').scrollTop($(this).scrollTop()); 
	$('#targetDiv').scrollLeft($(this).scrollLeft()); 
}); 
$('#targetDiv').scroll( function() { 
	$('#sourceDiv').scrollTop($(this).scrollTop()); 
	$('#sourceDiv').scrollLeft($(this).scrollLeft()); 
});
```