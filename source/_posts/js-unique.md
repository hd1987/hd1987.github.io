---
title: js数组去重的方法
date: 2018-10-22 09:11:42
categories:
  - Note
tags:
  - js
---

```js
Array.prototype.unique = function () {
  var r = []
  var n = {}

  for(var i = 0; i < this.length; i++) {
    var val = this[i]
    var type = typeof val

    if (!n[val]) {
      r.push(val)
      n[val] = [type]
    } else if (n[val].indexOf(type) < 0) {
      r.push(val)
      n[val].push(type)
    }
  }

  return r
}
```

```js
var arr = [112,112,34,'你好','112',112,34,'你好','str','str1', {}, {}, null, null]

arr.unique() // [112, 34, "你好", "112", "str", "str1", {…}, null]
```
