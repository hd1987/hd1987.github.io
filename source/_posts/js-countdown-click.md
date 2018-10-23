---
title: 点击倒计时countdown
date: 2017-05-09 16:14:16
tags: js
---

```js
// countdown
var $timeBox = $(".btn-verify"),
  setTime = 5, //set second
  paramTime,
  Message = {
    second: '秒后获取',
    verify: '获取验证码'
  };

function funTimeout() {
  paramTime--;

  $timeBox.html(paramTime + Message.second); //show

  if (paramTime == 0) {
    $timeBox.addClass('able').html(Message.verify);
  } else {
    setTimeout("funTimeout()", 1000);
  }

}

$(function () {

  $timeBox.on('click', function () {
    var $this = $(this);
    if ($this.hasClass('able')) {
      $this.removeClass('able');
      paramTime = setTime;
      funTimeout();
    }
  })

})
```

```html
<div class="btn-verify able">Click</div>
```


