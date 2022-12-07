---
title: 判断是否是微信内置浏览器
date: 2016-03-25 23:26:51
categories:
  - Note
tags:
  - js
---

``` js
function isWeiXin(){ 
  var ua = window.navigator.userAgent.toLowerCase();
  if(ua.match(/MicroMessenger/i) == 'micromessenger'){
    return true;
  }else{
    return false;
  }
}

$(function(){
  if(isWeiXin()){
    $("body").html("微信打开");
  }else {
    $("body").html("其它浏览器打开");
  }
})
```