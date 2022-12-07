---
title: git shallow clone
date: 2018-06-04 13:28:48
categories:
  - Note
tags:
  - git
---

`git clone` 默认会下载项目的完整历史版本，如果你只关心最新版的代码，而不关心之前的历史信息，可以使用 git 的浅复制功能：

```
$ git clone --depth=1 git@github.com:hd1987/hd1987.github.io.git
```

`--depth=1` 表示只下载最近一次的版本，使用浅复制可以大大减少下载的数据量，如果之后又想获取完整历史信息，可以使用下面的命令：

```
$ git fetch --unshallow
```
