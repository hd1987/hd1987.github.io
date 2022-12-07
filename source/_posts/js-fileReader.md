---
title: 图片上传预览, 通过file标签和js的FileReader接口
date: 2018-01-19 17:02:43
categories:
  - Note
tags:
  - js
---

用html的file标签就能实现图片上传前预览，就是通过file标签和js的FileReader接口，把选择的图片文件调用readAsDataURL方法，把图片数据转成base64字符串形式显示在页面上。

<!-- more -->

```js
<input type="file" id="xdaTanFileImg" onchange="xmTanUploadImg(this)" accept="image/*" />
<img id="xmTanImg" />
<script type="text/javascript">
  //判断浏览器是否支持FileReader接口
  if (typeof FileReader == 'undefined') {
    document.getElementById("xmTanDiv").InnerHTML = "<h1>当前浏览器不支持FileReader接口</h1>";
  }

  //选择图片，马上预览
  function xmTanUploadImg(obj) {
    var file = obj.files[0];

    console.log(obj);
    console.log(file);
    console.log("file.size = " + file.size); //file.size 单位为byte

    var reader = new FileReader();

    //读取文件过程方法
    reader.onloadstart = function (e) {
      console.log("开始读取....");
    }
    reader.onprogress = function (e) {
      console.log("正在读取中....");
    }
    reader.onabort = function (e) {
      console.log("中断读取....");
    }
    reader.onerror = function (e) {
      console.log("读取异常....");
    }
    reader.onload = function (e) {
      console.log("成功读取....");

      var img = document.getElementById("xmTanImg");
      img.src = e.target.result;
      //或者 img.src = this.result;  //e.target == this
    }

    reader.readAsDataURL(file)
  }
</script>
```
