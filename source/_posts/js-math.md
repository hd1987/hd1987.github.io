---
title: js Math取整，小数点保留后几位
date: 2022-12-16 09:11:42
categories:
  - Note
tags:
  - js
toc: true
---

js Math取整，小数点保留后几位

<!-- more -->

### 只保留整数部分（丢弃小数部分）
```js
parselnt(5.1234) // 5
```

### 向下取整（<=该数值的最大整数）和 parselnto一样
```js
Math.floor(5.1234) // 5
```

### 例小数点保留2位
```js
Math.floor(5.3456 * 100) / 100 // 5.34
```

### 向上取整（有小数，整数就+7）
```js
Math.ceil(5.1234) // 5
```

### 四舍五入（小数部分）
```js
Math.round(5.1234) // 5
Math.round(5.6789) // 6
```

### 绝对值
```js
Math.abs(-1) // 1
```

### 返回两者中的较大值
```js
Math.max(1,2) // 2
```

### 返回两者中的较小值
```js
Math.min(1,2) // 1
```
### 随机数 (0-1)
```js
Math.random()
```
