---
title: jquery倒计时页面跳转
date: 2016-03-25 23:57:13
tags: js
---

``` js
$(function(){
    funTimeout(); //应用倒计时
})
//倒计时
var strTime = 10; //设置时间
var strTimeBox = $(".time-box"); //数字容器
function funTimeout() {
    strTimeBox.html(strTime); //显示数字
    strTime--;
    if (strTime == 0) {
        window.opener = null;
        window.location.href = "http://www.baidu.com/";
    }
    else {
        setTimeout("show()", 1000);
    }
}
```