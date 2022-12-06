---
title: 移动端wap用到的头部信息代码meta
date: 2016-03-22 22:57:59
tags: [html, meta]
toc: true
---

### 禁止页面缩放

``` html
<meta content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0" name="viewport" />
```

### 禁止数字拨号功能

``` html
<meta name="format-detection" content="telephone=no">
<a href="tel:4008106999,1034">400-810-6999 转 1034</a>
```

<!--more-->

### 全屏模式运行

``` html
<meta name="apple-mobile-web-app-capable" content="yes">
```

### 顶部状态栏背景色（需全屏运行）

``` html
<meta name="apple-mobile-web-app-status-bar-style" content="black" />
```

### wap设置缓存

``` html
<meta http-equiv="Cache-Control" content="no-cache" />
```

### 桌面图标

``` html
<link rel="apple-touch-icon" href="touch-icon-iphone.png" />
<link rel="apple-touch-icon" sizes="76x76" href="touch-icon-ipad.png" />
<link rel="apple-touch-icon" sizes="120x120" href="touch-icon-iphone-retina.png" />
<link rel="apple-touch-icon" sizes="152x152" href="touch-icon-ipad-retina.png" />
```

### 启动画面

``` html
<link rel="apple-touch-startup-image" href="start.png"/>  

<!--iPhone-->
<link href="apple-touch-startup-image-320x460.png" media="(device-width: 320px)" rel="apple-touch-startup-image" />  

<!-- iPhone Retina -->
<link href="apple-touch-startup-image-640x920.png" media="(device-width: 320px) and (-webkit-device-pixel-ratio: 2)" rel="apple-touch-startup-image" />

<!-- iPhone 5 -->
<link rel="apple-touch-startup-image" media="(device-width: 320px) and (device-height: 568px) and (-webkit-device-pixel-ratio: 2)" href="apple-touch-startup-image-640x1096.png">

<!-- iPad portrait -->
<link href="apple-touch-startup-image-768x1004.png" media="(device-width: 768px) and (orientation: portrait)" rel="apple-touch-startup-image" />

<!-- iPad landscape -->
<link href="apple-touch-startup-image-748x1024.png" media="(device-width: 768px) and (orientation: landscape)" rel="apple-touch-startup-image" />

<!-- iPad Retina portrait -->
<link href="apple-touch-startup-image-1536x2008.png" media="(device-width: 1536px) and (orientation: portrait) and (-webkit-device-pixel-ratio: 2)" rel="apple-touch-startup-image" />

<!-- iPad Retina landscape -->
<link href="apple-touch-startup-image-1496x2048.png" media="(device-width: 1536px) and (orientation: landscape) and (-webkit-device-pixel-ratio: 2)" rel="apple-touch-startup-image" />
```