---
title: 当弹出popup悬浮层时，禁止body滚动
date: 2017-01-14 21:41:14
categories:
  - Note
tags:
  - js
---

示例：

```html
<!doctype html>
<html>
<head>
<meta charset="utf-8">
<meta name="format-detection" content="telephone=no">
<meta name="viewport" content="width=device-width,initial-scale=1.0,maximum-scale=1.0,user-scalable=0" />
<title>test</title>
<style>
p { line-height: 110px; }
.btn { position: fixed; top: 10px; right: 10px; z-index: 9; padding: 5px 10px; color: #fff; background: #c00; }
.mask { position: fixed; top: 0; right: 0; bottom: 0; left: 0; background: rgba(0,0,0,.5); z-index: 99; display: none; }
.popup { position: fixed; top: 0; right: 0; bottom: 0; left: 40px; background: #fff; z-index: 101; overflow-y: auto; display: none; }
</style>
</head>
<body>
  <div class="btn">Click</div>
  <div class="main"><p>111</p><p>222</p><p>333</p><p>444</p><p>555</p><p>666</p><p>777</p><p>888</p><p>999</p></div>
  <div class="mask"></div>
  <div class="popup"><p>111</p><p>222</p><p>333</p><p>444</p><p>555</p><p>666</p><p>777</p><p>888</p><p>999</p></div>
</body>
<script src="jquery-1.10.1.min.js"></script>
</html>
<script>
var $body = $('body'),
    scrollTop;

$('.btn').on('click', function() {
  $('.mask, .popup').show();
  scrollTop = $body.scrollTop(); //body设置为fixed之后会飘到顶部，所以要动态计算当前用户所在高度
  $body.css({
      'overflow':'hidden',
      'position': 'fixed',
      'top': scrollTop*-1
  });
});

$('.mask').on('click', function() {
  $('.mask, .popup').hide();
  /*取消后设置回来*/
  $body.css({
      'overflow':'auto',
      'position': 'static',
      'top': 'auto'
  }).animate({ scrollTop: scrollTop }, 0);
});

</script>
```


