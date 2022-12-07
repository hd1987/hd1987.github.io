---
title: jQuery插件的基本格式写法
date: 2016-09-27 23:46:55
categories:
  - Note
tags:
  - js
---

```js
(function($) {

  // funName 是控件名称
  $.fn.funName = function(options) {

    // 设置默认值
    var defaults = {
      choose: 'red',
      out: '#000'
    }

    // 如果options有的话就用options，或者使用default参数
    var options = $.extend(defaults, options);

    // 遍历 return 链式操作
    return this.each(function() { // 这里的this是jQuery对象

      var $this = $(this); // 这里的this是当前循环的dom

      // 例当前dom和同级其它dom分别添加颜色属性
      $this.css('color', options.choose).siblings().css('color', options.out);

    });

  }

})(jQuery);

$(function() {
  // 调用
  $('#demo').funName({'choose':'green', 'out':'#f00'});
});
```


