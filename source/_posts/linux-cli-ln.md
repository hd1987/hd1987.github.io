---
title: linux软链接创建、删除和更新
date: 2019-11-13 11:52:49
categories:
  - Note
tags:
  - linux
  - cli
toc: true
---

### 创建
```
ln -s 【目标目录】 【软链接地址】
ln -s /var/www/test test
```
软链接创建需要同级目录下没有同名的文件

### 删除
```
rm -rf 【软链接地址】
rm -rf test
```
软链接地址最后不能含有“/”，当含有“/”时，删除的是软链接目标目录下的资源，而不是软链接本身

### 修改
```
ln -snf 【新目标目录】 【软链接地址】
ln -snf /var/www text
```
这里修改是指修改软链接的目标目录
