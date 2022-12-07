---
title: js focus end
date: 2018-10-16 16:22:59
categories:
  - Note
tags:
  - js
---

```js
export let setFocus = (target) => {
  let t = jQuery(target).val()
  jQuery(target).val('').focus().val(t)
}
```

```js
setFocus('input')
```
