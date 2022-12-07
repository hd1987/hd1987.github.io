---
title: jquery天时分秒倒计时
date: 2016-03-25 23:59:01
categories:
  - Note
tags:
  - js
---

html
``` html
<div class="get-rt-time" data-time="2100-11-11 20:20:20"></div>
<div class="get-rt-time" data-time="2015-11-11 20:20:20"></div>
```

js
``` js
$(function(){
  $.fn.funTime=function(msg){
    var data="";
    var _DOM=null;
    var funDom = function(dom){
      _DOM=dom;
      data=$(dom).attr("data-time");
      data = data.replace(/-/g,"/");
      data = Math.round((new Date(data)).getTime()/1000);
      var domTHML = '<em class="myday"></em><em class="split">天</em>'+
        '<em class="myhour"></em><em class="split">时</em>'+
        '<em class="mymin"></em><em class="split">分</em>'+
        '<em class="mysec"></em><em class="split">秒</em>';
      $(_DOM).append(domTHML);
      funMsg(msg);
    };
    var funMsg = function(msg){
      var	range  	= data-Math.round((new Date()).getTime()/1000),
        secday = 86400, sechour = 3600,
        days 	= parseInt(range/secday),
        hours	= parseInt((range%secday)/sechour),
        min		= parseInt(((range%secday)%sechour)/60),
        sec		= ((range%secday)%sechour)%60;
      if(hours < 10)
        hours = "0" + hours;
      if(min < 10)
        min = "0" + min;
      if(sec < 10)
        sec = "0" + sec;
      if(hours>0||min>0||sec>0){
        $(_DOM).find(".myday").html(days);
        $(_DOM).find(".myhour").html(hours);
        $(_DOM).find(".mymin").html(min);
        $(_DOM).find(".mysec").html(sec);
      }else{
        $(_DOM).hide();
        $(_DOM).after(msg);
      }
    };
    setInterval( funMsg,1000 );

    return this.each(function(){
      var $this = $(this);
      funDom($this);
    });
  }

  //应用
  $(".get-rt-time").each(function(){
    var msg='<div class="mask_end"><span>活动结束</span></div>';
    $(this).funTime(msg);
  });
});
```