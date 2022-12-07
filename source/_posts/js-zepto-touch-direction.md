---
title: zepto判断左右滑动
date: 2016-03-26 00:02:39
categories:
  - Note
tags:
    - js
    - zepto
---

``` js
var startPosition, endPosition, deltaX, deltaY, moveLength;
        $(".content").bind('touchstart', function(e){
            var touch = e.touches[0];
            startPosition = {
                x: touch.pageX,
                y: touch.pageY
            }
        }) .bind('touchmove', function(e){
            var touch = e.touches[0];
            endPosition = {
                x: touch.pageX,
                y: touch.pageY
            };

            deltaX = endPosition.x - startPosition.x;
            deltaY = endPosition.y - startPosition.y;
            moveLength = Math.sqrt(Math.pow(Math.abs(deltaX), 2) + Math.pow(Math.abs(deltaY), 2));
        }).bind('touchend', function(e){
            if(deltaX < 0) { // 向左划动
                console.log("向左划动");
            } else if (deltaX > 0) { // 向右划动
                console.log("向右划动");
            }
        });
```

