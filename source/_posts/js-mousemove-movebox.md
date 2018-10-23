---
title: 跟随鼠标移动的悬浮提示框案例
date: 2016-03-25 23:48:55
tags: js
---

js部分
``` js
$(function(){
	$('<div id="tip_box"></div>').appendTo(document.body);
	$(".mhover li").each(function (i) {
		$(this).mousemove(function (ev) {
			var str = $(this).data("ori");
			var box = $('#tip_box');
			box.show();
			box.html(str);
			var t = $(window).scrollTop();
			var x = ev.clientX - box.width() - 40;
			var y = ev.clientY + t - 15;
			box.css({ left: x, top: y });
		});
		$(this).mouseout(function () {
			$("#tip_box").hide();
		});
	});
})
```

html部分
``` html
<style type="text/css">
	* { margin:0; padding:0; list-style:none;}
	.mhover { margin: 50px auto 0; width:200px; border:solid 1px #ccc;}
	.mhover li { height:30px; line-height:30px;}
	#tip_box { position:absolute; top:0; left:0; background:#f00;}
</style>

<div class="mhover">
	<ul>
		<li data-ori="这里是需要显示的文字1">标题</li>
		<li data-ori="这里是需要显示的文字2">标题</li>
		<li data-ori="这里是需要显示的文字3">标题</li>
		<li data-ori="这里是需要显示的文字4">标题</li>
		<li data-ori="这里是需要显示的文字5">标题</li>
		<li data-ori="这里是需要显示的文字6">标题</li>
		<li data-ori="这里是需要显示的文字7">标题</li>
		<li data-ori="这里是需要显示的文字8">标题</li>
		<li data-ori="这里是需要显示的文字9">标题</li>
	</ul>
</div>
```