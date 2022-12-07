---
title: IE6 png图片透明的2种方法
date: 2016-03-25 08:58:45
categories:
  - Note
tags:
   - css
   - js
---

一.图片当背景，CSS方法

``` css
img {
    _background:none;  
    _filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(src='logo.png',sizingMethod='crop');
    }
```

但是测试发现当给background:red url(logo.png) no-repeat center;加了红色时，别的浏览器正常识别，ie6会出现依旧不识别的情况。
解决办法是在外面套的标签，或body加背景色。（background-color:red;单独写就可以了）
强调：IE6做了透明的背景，对他上面`<A>`便签会失效，也就是点有连接的地方没连接了，解决方案：
列`<div class="top"><a>首页</a> <a>关于我们</a> <a>产品中心</a>...</div>`，如果top这个class有PNG背景，而你又用了我那个代码，这个时候里面的链接会没反映的，解决就是:
`.top a{position:relative}`，这个很常用了

<!--more-->

二.图片插入，也就是`<img src="" />`这种形式，试用JS方法

``` js
<script>
function correctPNG()
   {
   for(var i=0; i<document.images.length; i++)
      {
     var img = document.images[i]
     var imgName = img.src.toUpperCase()
     if (imgName.substring(imgName.length-3, imgName.length) == "PNG")
        {
       var imgID = (img.id) ? "id='" + img.id + "' " : ""
       var imgClass = (img.className) ? " " : ""
       var imgTitle = (img.title) ? "title='" + img.title + "' " : "title='" + img.alt + "' "
       var imgStyle = "display:inline-block;" + img.style.cssText
       if (img.align == "left") imgStyle = "float:left;" + imgStyle
       if (img.align == "right") imgStyle = "float:right;" + imgStyle
       if (img.parentElement.href) imgStyle = "cursor:hand;" + imgStyle      
       var strNewHTML = "<span " + imgID + imgClass + imgTitle
       + " style=\"" + "width:" + img.width + "px; height:" + img.height + "px;" + imgStyle + ";"
        + "filter:progid:DXImageTransform.Microsoft.AlphaImageLoader"
       + "(src=\'" + img.src + "\', sizingMethod='scale');\"></span>"
       img.outerHTML = strNewHTML
       i = i-1
        }
      }
   }
window.attachEvent("onload", correctPNG);

if (navigator.platform == "Win32" && navigator.appName == "Microsoft Internet Explorer" && window.attachEvent) {
   window.attachEvent("onload", alphaBackgrounds);
}
function alphaBackgrounds(){
   var rslt = navigator.appVersion.match(/MSIE (d+.d+)/, '');
   var itsAllGood = (rslt != null && Number(rslt[1]) >= 5.5);
   for (i=0; i<document.all.length; i++){
      var bg = document.all[i].currentStyle.backgroundImage;
      if (itsAllGood && bg){
         if (bg.match(/.png/i) != null){
            var mypng = bg.substring(5,bg.length-2);
            document.all[i].style.filter = "progid:DXImageTransform.Microsoft.AlphaImageLoader(src='"+mypng+"', sizingMethod='scale')";
            document.all[i].style.backgroundImage = "url('')";
         }                                                
      }
   }
}
alphaBackgrounds();
</script>
```
