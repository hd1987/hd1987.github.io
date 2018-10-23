---
title: hexo常用命令笔记
date: 2016-04-14 22:15:26
tags: hexo
---

### 简写
hexo n == hexo new
hexo p == hexo publish
hexo g == hexo generate
hexo s == hexo server
hexo d == hexo deploy

<!--more-->

### 服务器
hexo server #Hexo 会监视文件变动并自动更新，您无须重启服务器。
hexo server -s #静态模式
hexo server -p 5000 #更改端口
hexo server -i 192.168.1.1 #自定义 IP
hexo clean #清除缓存 网页正常情况下可以忽略此条命令
hexo g #生成静态网页
hexo d #开始部署
hexo algolia #生成静态网页 (接入algolia后用于生成文件和搜索)

### 监视文件变动
hexo generate #使用 Hexo 生成静态文件快速而且简单
hexo generate --watch #监视文件变动

### 完成后部署
两个命令的作用是相同的
hexo generate --deploy hexo deploy --generate
hexo deploy -g hexo server -g

### 草稿
hexo publish [layout] &lt;title&gt;

### 模版
hexo new "postName" #新建文章
hexo new page "pageName" #新建页面
hexo generate #生成静态页面至public目录
hexo server #开启预览访问端口（默认端口4000，'ctrl + c'关闭server）
hexo deploy #将.deploy目录部署到GitHub

`hexo new [layout] <title> hexo new photo "My Gallery" hexo new "Hello World" --lang tw`

变量 | 描述
----- | -----
layout | 布局
title | 标题
date | 文件建立日期

``` hexo
title: 使用Hexo搭建个人博客
layout: post
date: 2014-03-03 19:07:43
comments: true
categories: Blog
tags: [Hexo]
keywords: Hexo, Blog
description: 生命在于折腾，又把博客折腾到Hexo了。给Hexo点赞。
```
### 模版（Scaffold）
hexo new photo &quot;My Gallery&quot;

变量 | 描述
----- | -----
layout | 布局
title | 标题
date | 文件建立日期

### 写作
`hexo new page <title> hexo new post <title>`

变量 | 描述
----- | -----
:title | 标题
:year | 建立的年份（4 位数）
:month | 建立的月份（2 位数）
:i_month | 建立的月份（去掉开头的零）
:day | 建立的日期（2 位数）
:i_day | 建立的日期（去掉开头的零）

### 推送到服务器上
hexo n #写文章
hexo g #生成
hexo d #部署 #可与 hexo g 合并为 hexo d -g

### 报错
`ERROR Deployer not found: git`
npm install hexo-deployer-git --save


