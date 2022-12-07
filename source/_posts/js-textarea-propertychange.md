---
title: 监听textarea的值的变化"propertychange"
date: 2016-03-25 23:52:08
categories:
  - Note
tags:
  - js
---

js示例
``` js
<textarea onpropertychange="if(value.length>100) value=value.substr(0,100)"></textarea>
```

jquery示例
``` js
function funTestarea(){
  var $testarea = $(".textarea textarea");
  var $b = $(".textarea b");
  $testarea.on("input propertychange",function(){
    var $this = $(this);
    var strNum = $.trim($this.val()).length;
    if(strNum>100){
      $(this).val($(this).val().substr(0,100));
    }else {
      $b.text(strNum);
    }
  });
}
```