---
title: git 修改本地和远程分支名称
date: 2021-10-20 13:18:00
tags: git
---

`git branch -a`  #查看所有分支
`git branch -r`  #查看远程分支
`git branch -vv`  #查看本地分支所关联的远程分支

`git branch -m old_branch new_branch`  #重命名本地分支
`git push origin :old_branch`  #删除远程分支
`git push --set-upstream origin new_branch`  #推送并关联新的远程分支
