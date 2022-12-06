---
title: Git 忽略文件不加入版本控制
date: 2018-05-28 14:27:59
tags: git
toc: true
---

## .gitignore

```
# 此为注释 – 将被 Git 忽略
*.a         # 忽略所有 .a 结尾的文件
!lib.a      # 但 lib.a 除外
/TODO       # 仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
build/      # 忽略 build/ 目录下的所有文件
doc/*.txt   # 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
tmp/*       # 忽略tmp文件夹所有文件，因为git不会加入空目录
```

其它过滤条件

* `？` : 代表任意的一个字符
* `＊` : 代表任意数目的字符
* `{!ab}` : 必须不是此类型
* `{ab,bb,cx}` : 代表ab,bb,cx中任一类型即可
* `[abc]` : 代表a,b,c中任一字符即可
* `[ ^abc]` : 代表必须不是a,b,c中任一字符

## .gitignoreglobal

在用户目录下创建 `~/.gitignoreglobal` 文件,  
需要执行 `git config --global core.excludesfile ~/.gitignoreglobal` 来使得它生效。

## 忽略本地的文件控制，不影响全局

`.git/info/exclude` 这里设置的是你自己本地需要排除的文件，他不会影响到其他人，也不会提交到版本库中去。

## 去除已经提交文件的版本控制（公共）

1. `rm -rf PATH`
2. `git rm -r --cached PATH`
3. 修改`.gitignore`，添加忽略文件
4. `git add -A`
5. `git push`

## 忽略已经提交到版本库的文件（本地）

`git update-index --assume-unchanged PATH`      # 忽略跟踪
`git update-index --no-assume-unchanged PATH`   #恢复跟踪

## 提交空的目录树

需要提交一个空的 log 目录时，在里面放置一个空的`.gitignore`