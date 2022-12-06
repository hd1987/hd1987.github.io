---
title: 文字超出范围以省略号表示 
date: 2016-03-24 22:30:54
tags: css
toc: true
---

### 一、单行溢出，超出部分显示...或者截取。前提必须有宽度。
``` css
p { width:100px; overflow:hidden; white-space:nowrap; text-overflow:ellipsis;}
```

<!--more-->

### 二、多行溢出
``` css
p { display:-webkit-box; overflow:hidden; text-overflow:ellipsis; -webkit-line-clamp:2; -webkit-box-orient:vertical;}
```

适用范围：
因使用了WebKit的CSS扩展属性，该方法适用于WebKit浏览器及移动端；
说明：
1.-webkit-line-clamp用来限制在一个块元素显示的文本的行数。 为了实现该效果，它需要组合其他的WebKit属性。常见结合属性：
2.display: -webkit-box; 必须结合的属性 ，将对象作为弹性伸缩盒子模型显示 。
3.-webkit-box-orient 必须结合的属性 ，设置或检索伸缩盒对象的子元素的排列方式 。

### 三、移动端
``` css
p{position: relative; line-height: 20px; max-height: 40px;overflow: hidden;}   
p::after{content: "..."; position: absolute; bottombottom: 0; rightright: 0; padding-left: 40px;   
background: -webkit-linear-gradient(left, transparent, #fff 55%);   
background: -o-linear-gradient(rightright, transparent, #fff 55%);   
background: -moz-linear-gradient(rightright, transparent, #fff 55%);   
background: linear-gradient(to rightright, transparent, #fff 55%);   
}
```

适用范围：
该方法适用范围广，但文字未超出行的情况下也会出现省略号,可结合js优化该方法。
说明：
1.将height设置为line-height的整数倍，防止超出的文字露出。
2.给p::after添加渐变背景可避免文字只显示一半。
3.由于ie6-7不显示content内容，所以要添加标签兼容ie6-7`（如：<span>…<span/>）`；兼容ie8需要将::after替换成:after。