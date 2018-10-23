---
title: div设置最小高度（兼容IE6）
date: 2016-03-25 08:40:43
tags: css
---

``` css
.test {
    height:auto!important;
    height:200px;
    min-height:200px;
}
```

标准浏览器中固定高度值的容器是不会象IE6里那样被撑开的,那我又想固定高度，又想能被撑开需要怎样设置呢？办法就是去掉height设置min-height:200px;  这里为了照顾不认识min-height的IE6 可以这样定义