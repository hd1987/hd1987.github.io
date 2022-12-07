---
title: js获取url参数方法
date: 2018-08-28 14:51:40
categories:
  - Note
tags:
  - js
---

```js
export let getUrlParam = (name) => {
  let reg = new RegExp('(^|&)' + name + '=([^&]*)(&|$)')
  let r = window.location.search.substr(1).match(reg)

  if (r != null) {
    return decodeURI(r[2])
  } else {
    return null
  }
}

```
