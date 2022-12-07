---
title: js链式取值（函数解析字符串）
date: 2018-10-15 22:58:34
categories:
  - Note
tags:
  - js
---

开发中，链式取值是非常正常的操作，如：  
`res.data.goods.list[0].price`  
有时候会出现错误：  
`Uncaught TypeError: Cannot read property 'goods' of undefined`

#### 通过函数解析字符串验证

```js
function get(obj, props, def) {
  if ((obj == null) || obj == null || typeof props !== 'string') return def;

  const temp = props.split('.');
  const fieldArr = [].concat(temp);

  temp.forEach((e, i) => {
    if (/^(\w+)\[(\w+)\]$/.test(e)) {
      const matchs = e.match(/^(\w+)\[(\w+)\]$/);
      const field1 = matchs[1];
      const field2 = matchs[2];
      const index = fieldArr.indexOf(e);
      fieldArr.splice(index, 1, field1, field2);
    }
  })

  return fieldArr.reduce((pre, cur) => {
    const target = pre[cur] || def;

    if (target instanceof Array) {
      return [].concat(target);
    }
    if (target instanceof Object) {
      return Object.assign({}, target)
    }
    return target;
  }, obj)
}
```

使用:

    var c = {
      a: {
        b: [1, 2, 3]
      }
    }
    get(c, 'a.b') // [1,2,3]
    get(c, 'a.b[1]') // 2
    get(c, 'a.d', 12) // 12