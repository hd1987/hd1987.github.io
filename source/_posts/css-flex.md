---
title: css3 flex弹性布局摘要
date: 2018-08-07 11:13:17
tags: css
---

Flex是Flexible Box的缩写，意为”弹性布局”，用来为盒状模型提供最大的灵活性

> 设为Flex布局以后，子元素的`float`、`clear`和`vertical-align`属性将失效

``` css
.box{
  display: -webkit-flex;  /* -webkit */
  display: flex;
  flex-direction: row | row-reverse | column | column-reverse;  /* row */
  flex-wrap: nowrap | wrap | wrap-reverse;  /* nowrap */
  flex-flow: <flex-direction> || <flex-wrap>;  /* row nowrap */
  justify-content: flex-start | flex-end | center | space-between | space-around;  /* flex-start */
  align-items: flex-start | flex-end | center | baseline | stretch;  /* stretch */
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;  /* stretch */
}

.item {
  order: <integer>;  /* 0 */
  flex-grow: <number>;   /* 0 */
  flex-shrink: <number>;  /* 1 */
  flex-basis: <length> | auto;  /* auto */
  flex: none | [ <'flex-grow'> <'flex-shrink'>? || <'flex-basis'> ];  /* 0 1 auto */
  align-self: auto | flex-start | flex-end | center | baseline | stretch;  /* auto */
}
```

<!-- more -->

# 容器属性

## flex-direction

决定主轴的方向（即项目的排列方向）

> `row`（默认值）: 主轴为水平方向，起点在左端
> `row-reverse`: 主轴为水平方向，起点在右端
> `column`: 主轴为垂直方向，起点在上沿
> `column-reverse`: 主轴为垂直方向，起点在下沿

## flex-wrap

如果一条轴线排不下，如何换行

> `nowrap`（默认）: 不换行
> `wrap`: 换行，第一行在上方
> `wrap-reverse`: 换行，第一行在下方

## flex-flow

是`flex-direction`属性和`flex-wrap`属性的简写形式

> 默认值为row nowrap

## justify-content

项目在主轴上的对齐方式

> `flex-start`（默认值）: 左对齐
> `flex-end`: 右对齐
> `center`:  居中
> `space-between`: 两端对齐，项目之间的间隔都相等
> `space-around`: 每个项目两侧的间隔相等，项目之间的间隔比项目与边框的间隔大一倍

## align-items

项目在交叉轴上如何对齐

> `flex-start`: 顶部对齐
> `flex-end`: 底部对齐
> `center`: 中间对齐
> `baseline`: 项目的第一行文字的基线对齐
> `stretch`（默认值）: 如果项目未设置高度或设为auto，将占满整个容器的高度

## align-content

多根轴线的对齐方式  
如果项目只有一根轴线，该属性不起作用

> `flex-start`: 顶部对齐
> `flex-end`: 底部对齐
> `center`: 中间对齐
> `space-between`: 与交叉轴两端对齐，轴线之间的间隔平均分布
> `space-around`: 每根轴线两侧的间隔都相等，轴线之间的间隔比轴线与边框的间隔大一倍
> `stretch`（默认值）: 轴线占满整个交叉轴


# 项目属性

## order

> 默认为0

项目的排列顺序  
数值越小，排列越靠前

## flex-grow
> 默认为0, 即如果存在剩余空间，也不放大

项目的放大比例

如果所有项目的flex-grow属性都为1，则它们将等分剩余空间（如果有的话），如果一个项目的flex-grow属性为2，其他项目都为1，则前者占据的剩余空间将比其他项多一倍

## flex-shrink
> 默认为1，即如果空间不足，该项目将缩小

项目的缩小比例

如果所有项目的flex-shrink属性都为1，当空间不足时，都将等比例缩小，如果一个项目的flex-shrink属性为0，其他项目都为1，则空间不足时，前者不缩小  
负值对该属性无效

## flex-basis
> 默认值为auto，即项目的本来大小

在分配多余空间之前，项目占据的主轴空间（main size），浏览器根据这个属性，计算主轴是否有多余空间  
它可以设为跟width或height属性一样的值（比如350px），则项目将占据固定空间

## flex

> 默认值为0 1 auto，后两个属性可选

flex属性是`flex-grow`, `flex-shrink` 和 `flex-basis`的简写

## align-self
> 默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch

允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性  
该属性可能取6个值，除了auto，其他都与align-items属性完全一致