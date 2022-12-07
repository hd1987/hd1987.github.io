---
title: retinajs使用摘要
date: 2016-10-04 09:01:17
categories:
  - Note
tags:
  - js
  - retina
---

官方文档：[retinajs](https://github.com/imulus/retinajs)

注：需要准备的图片名称格式

> image.png
> image@2x.png
> image@3x.png

现在有4种实现方式：
1. 自动交换“img”标签的"src"路径。
2. 在内联样式中自动交换背景图像的网址。
3. 手动指定一个高分辨率的图像不同位置。
4. 自动创建CSS背景图像媒体查询。

<!-- more -->

```html
// 自动交换
<img src="/images/my_image.png" data-rjs="3" />
<div style="background: url(my_image.png);" data-rjs="3" />
// 手动指定路径
<img src="/images/my_image.png" data-rjs="/images/2x/my_image.png" />
```

把"data-rjs"的属性值设为3，就相当于你告知了retina.js您已创建了比传统像素密度大3倍的高分辨率图像（包括@2x和@3x的图片）。


## SCSS, Sass, LESS, and Stylus

css预处理是在样式表中提供高分辨率的图片，每一种预处理机制，都有4个参数：

> 1.path - 你的标准分辨率图像的路径。
> 2.cap - 您准备的最高分辨率图片的等级。默认为2。
> 3.size - background-size的属性值。默认为auto auto。
> 4.extras - 任何其他背景属性的属性值。默认没有。

步骤：

1.添加 retina mixin到你的样式表中。
2.在你的样式表中，调用retina mixin,而不是使用 background-image

```css
// SCSS
#logo {
  @include retina('my_image.png', 3, 100px 50px, center center no-repeat);
}

// Sass
#logo
+retina ('my_image.png', 3, 100px 50px, center center no-repeat); 

// Less
#logo {
  .retina('my_image.png', 3, 100px 50px, center center no-repeat);
}
　
// Stylus
#logo
  retina('my_image.png', 3, 100px 50px, center center no-repeat);
```

编译成：

```css
#logo {
  background: url("my_image.png") center center no-repeat;
  background-size: 100px 50px;
}

@media all and (-webkit-min-device-pixel-ratio: 1.5),
       all and (-o-min-device-pixel-ratio: 3 / 2),
       all and (min--moz-device-pixel-ratio: 1.5),
       all and (min-device-pixel-ratio: 1.5) {
  #item {
    background: url("my_image@2x.png") center center no-repeat;
    background-size: 100px 50px;
  }
}

@media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
  #item {
    background: url("my_image@2x.png") center center no-repeat;
    background-size: 100px 50px;
  }
}

@media (-webkit-min-device-pixel-ratio: 3), (min-resolution: 288dpi) {
  #item {
    background: url("my_image@3x.png") center center no-repeat;
    background-size: 100px 50px;
  }
}
```


