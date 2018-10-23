---
title: base.css
date: 2016-10-10 22:59:44
tags: css
---

常用的base.css初始化样式

```css

@charset "UTF-8";
* {
  margin: 0;
  padding: 0;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  -webkit-tap-highlight-color: transparent;
}

html, body {
  color: #333;
  background: #fff;
  line-height: 1.2;
}

a {
  color: #D7171F;
}

a:hover {
  color: #D7171F;
  text-decoration: none;
}

html {
  -webkit-font-smoothing: antialiased;
}

body,
button,
input,
select,
textarea {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 16px;
}

button,
input,
select {
  vertical-align: middle;
  outline: none;
}

textarea {
  outline: none;
  resize: none;
}

input::-webkit-input-placeholder,
textarea::-webkit-input-placeholder {
  color: #b3b3b3;
}

input:-moz-placeholder,
textarea:-moz-placeholder {
  color: #b3b3b3;
}

input::-moz-placeholder,
textarea::-moz-placeholder {
  color: #b3b3b3;
}

input:-ms-input-placeholder,
textarea:-ms-input-placeholder {
  color: #b3b3b3;
}

/*::-webkit-scrollbar{width:5px;}
::-webkit-scrollbar-track{background-color:#fff;}
::-webkit-scrollbar-thumb{background-color:#ccc; border-radius:4px;}
::-webkit-scrollbar-thumb:hover {background-color:#ccc}
::-webkit-scrollbar-thumb:active {background-color:#ccc}*/

table {
  border-collapse: collapse;
  border-spacing: 0;
}

img {
  border: 0;
}

ol,
ul {
  list-style: none;
}

.clearfix:after {
  visibility: hidden;
  display: block;
  font-size: 0;
  content: " ";
  clear: both;
  height: 0;
}

```


