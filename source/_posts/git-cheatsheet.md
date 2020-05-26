---
title: git cheatsheet 中文速查表 (2019/09/16)
date: 2020-05-25 13:35:16
tags: git
---

## 配置
```sh
git config --global "Your Name"
git config --global "Email Address"
```

## 初始化
```sh
git init
```

## 提交修改
```sh
git add <file>
git add -u 提交work directory中所有已track的文件至staging area
git commit -m "descriptions"
git commit --amend 对最近一次的提交做内容修改
git commit --amend --author "user_name <user_email>" 修改最近提交用户名和邮箱
```

<!-- more -->

## 查看状态、比对
```sh
git status
git status -s 文件状态缩略信息, 常见 A:新增; M:文件变更; ?:未track; D:删除
git diff <file>
git diff HEAD -- <file>		查看工作区和版本库里面最新版本的区别
git diff --check <file>     检查是否有空白错误(regex:' \{1,\}$')
git diff --cached <file>    查看已add的内容(绿M)
```

## 查看历史版本、历史操作
```sh
git log
git reflog
git log -n                  最近n条的提交历史
git log <branch_name> -n    分支branch_name最近n条的提交历史
git log --stat              历次commit的文件变化
git log lhs_hash..rhs_hash  对比两次commit的变化(增删的主语为lhs, 如git log HEAD~2..HEAD == git log HEAD -3)
git log -p                  历次commit的内容增删
git log -p -W               历次commit的内容增删, 同时显示变更内容的上下文
git log origin/EI-1024 -1 --stat -p -W 查看远端分支EI-1024前一次修改的详细内容
git log origin/master..dev --stat -p -W 查看本地dev分支比远端master分支变化(修改)的详细内容

git log <branch_name> --oneline   对提交历史单行排列
git log <branch_name> --graph     对提交历史图形化排列
git log <branch_name> --decorate  对提交历史关联相关引用, 如tag, 本地远程分支等
git log <branch_name> --oneline --graph --decorate 拼接一下, 树形化显示历史
git log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen%ai(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit 同上, 建议alais保存

git log --since --after     显示时间之后的提交
git log --until --before    显示时间之前的提交
git log --author                显示指定作者的提交
git log --committer             显示指定committer的提交(注:committer不一定是author)
git log origin/b3.3/master --author=yx-ren --since="2019-10-01" --before="2019-11-01" 查看某作者在某发布版本最近一个月的提交, 常见于线上背锅
git log origin/b3.0/master --author=some_leave --since="1 month ago" 查看某刚离职同事过去一个月的提交, 常见于背锅
git log --since=1.weeks     过去一周的提交(写周报的时候可以看看我这一周干了啥)
git log --since=1.days      过去一天的提交(下班的时候可以看看我这一天干了啥)
git log --since="1 weeks 2 days 3 hours 40 minutes 50 seconds ago" 过去1周2天3小时40分50秒之内的提交
```

## 版本回退、前进
```sh
git reset --hard HEAD^		回退到上1版本
git reset --hard HEAD~5		回退到上5个版本
git reset --hard id		回退到指定版本
```

## 撤销修改
```sh
git checkout -- <file>		撤销修改：误修改工作区文件，未git add/commit
git restore <file>		撤销修改：误修改工作区文件，未git add/commit
git reset HEAD <file>		撤销git add：误将文件加入暂存区（git add），未git commit
git reset --hard HEAD^		撤销git commit：误将文件提交（一旦提交，只能通过版本回退进行撤销）
```

## 删除与恢复
```sh
git rm/add <file>
git commit -m "remove <file>"	删除版本库中的<file>：删除工作区文件后，继续删除版本库中相应的文件
git checkout -- <file>		根据版本库中的<file>恢复工作区<file>
```

## 关联GitHub远程仓库（本地到远程）
```sh
git remote add origin <remote address>	在本地工作区目录下按照 GitHub 提示进行关联
git remote rm origin			解除错误关联
git push -u origin master		第一次将本地仓库推送至远程仓库（每次在本地提交后进行操作）
git push origin master			以后每次将本地仓库推送至远程仓库（每次在本地提交后进行操作）
<remote address>:
	git@github.com:<username>/<repository>.git
	https://github.com/<username>/<repository>.git
```

## 克隆GitHub远程仓库（远程到本地）
```sh
git clone <remote address>	git协议速度更快但通常公司内网不允许，https协议速度慢
```

## 分支管理：创建、切换、查看、合并、删除
```sh
git branch <branch name>	创建<branch name>分支
git checkout <branch name>	切换至<branch name>分支
git switch <branch name>	切换至<branch name>分支
git checkout -b <branch name>	创建并切换至<branch name>分支
git switch -c <branch name>	创建并切换至<branch name>分支
git branch			查看已有分支（* 表示当前分支）
git merge <branch name>		合并<branch name>到当前分支（通常在master分支下操作）
git branch -d <branch name>	删除分支
```

## 解决合并冲突
```sh
合并时报错“分支发生冲突”，首先vim相应文件，修改冲突位置，然后按照git add/commit重新提交，最后删除多余分支即可。
git log --graph --pretty=oneline --abbrev-commit
git log --graph
```

## 分支管理：合并后删除分支也在 log 中保留分支记录
```sh
git merge --no-ff -m "descriptions" <branch name>
```

## 开发流程：
```sh
master分支		发布稳定版本
dev分支			发布开发版本
<developer name>分支	个人开发分支（个人开发完成将该分支并入dev，同时保留该分支，继续开发）
```


## Bug分支管理（建立单独分支进行bug修复）
```sh
软件开发中，bug就像家常便饭一样。有了bug就需要修复，在Git中，由于分支是如此的强大，所以，每个bug都可以通过一个新的临时分支来修复，修复后，合并分支，然后将临时分支删除。
git stash			保存当前工作现场（在dev未完成开发，但master有bug需要修复）
git stash pop			回到dev分支后恢复工作现场（list中的现场会同时被删除）
git stash list			查看当前存储的工作现场
git stash apply stash@{#}	回到指定工作现场（list中的现场不会被删除，需要用git stash drop）
git stash drop stash@{#}	删除指定工作现场
git cherry-pick <id>		在master修复好bug后，在dev复制一遍bug修复流程
```

## Feature分支管理（建立单独分支添加新功能）
```sh
软件开发中，总有无穷无尽的新的功能要不断添加进来。添加一个新功能时，你肯定不希望因为一些实验性质的代码，把主分支搞乱了，所以，每添加一个新功能，最好新建一个feature分支，在上面开发，完成后，合并，最后，删除该feature分支。
git branch -D <branch name>	强制删除分支（丢弃未合并分支）
```

## 协作与分支推送
```sh
User 1:
git remote [-v]						查看远程库信息（-v 查看详细信息）
git push origin [master/dev/...]			推送指定分支到远程
User 2:
git clone <remote address>				克隆到本地（只能克隆master）
git checkout -b dev origin/dev				本地新建分支并关联远程
git add/commit/push					添加、提交、推送更新
User 1:
git add/commit/push					推送时报错（与user 2推送的更新冲突）
git pull <remote> <branch>
git branch --set-upstream-to=origin/<branch> <branch>	本地与远程关联
git pull						拉取远程文件（并解决冲突）
git commit/push						重新提交并推送
```

## 标签管理（常用于版本管理）：查看、创建、操作
```sh
git tag								查看标签
git show <tag name>						查看指定标签
git log --pretty=oneline --abbrev-commit --decorate=full	在log中显示标签
git tag <tag name>						为上次commit位置打标签
git tag <tag name> <commit id>					为指定commit位置打标签
git tag -a <tag name> -m "descriptions" <commit id>		为指定commit打标并添加描述
git tag -d <tag name>						删除本地标签
git push origin <tag name>					推送指定标签到远程
git push origin --tags						推送所有本地标签到远程
git push origin :refs/tags/<tag name>				删除远程标签（先删除本地标签）
```

## rebase(换基)
```sh
# rebase 在日常中常用功能主要是两个, 多人协同开发定期rebase master以及压缩某分支多个commit
git rebase master 常见于多人开发, 每个开发人员从master checkout出自己的分支, 开发一段时间后提交至master之前最好rebase一下, 防止冲突,就算真有冲突在本地解决好过强制提交, 开发流程中尽量保证master的干净整洁
git rebase -i HEAD~n 压缩当前分支的n个commit并合并为1个commit, 常见第一行为pick, 剩下的n-1行为squash
git rebase --abort # rebase过程中发生错误, 可以利用该命令终止整个rebase过程
git rebase --continue # rebase过程中发生冲突, 在解决冲突后可以利用该命令进行后续过程
```

## 打patch(补丁)
```sh
# 生成diff patch文件(git可以识别diff文件)
git <branch> log -n -p > diff.patch # 生成某分支过去n个commit的文件diff信息至单个diff文件
git diff <--cached> diff.patch # 针对当前缓存区的内容生成diff文件

# 利用apply打patch
git apply --check diff.patch    #检查是否可以正常应用, 无回显证明无冲突
git apply --stat diff.patch     #查看应用diff文件后的文件变化
git apply diff.patch            #打patch, 仅仅改变文件信息, 无commit信息, 仍然需要add, commit

# 利用--format-patch生成patch, 带commit信息
git format-patch <branch> -n 　 #生成分支<branch>最近的n次commit的patch
git format-patch <r1>..<r2>     #生成两个commit间的修改的patch（包含两个commit. <r1>和<r2>都是具体的commit号)
git format-patch -1 <r1>        #生成单个commit的patch
git format-patch <r1>           #生成某commit以来的修改patch（不包含该commit）
git format-patch --root <r1>　　#生成从根到r1提交的所有patch

# 利用am打patch
git apply --check 0001-update-bash.sh.patch #检查patch是否冲突可用
git apply --stat 0001-update-bash.sh.patch  #检查patch文件变更情况, 无回显证明无冲突
git am 0001-update-bash.sh.patch            #将该patch打上到当前分支, 带commit信息
git am ./*.patch                            #将当前路径下的所有patch按照先后顺序打上
git am --abort                              #终止整个打patch的过程, 类似rebase --abort
git am --resolved                           #解决冲突后, 可以执行该命令进行后续的patch, 类似rebase --continue
```

## 使用GitHub
```sh
fork --> clone --> add/commit/push --> pull request
```

## 其他配置
```sh
git config --global color.ui true	显示颜色
```

## 配置.gitignore文件
```sh
/<dir name>/			忽略文件夹
*.zip				忽略.zip文件
/<dir name>/<file name>		忽略指定文件
```

## 文件.gitignore生效后
```sh
git add -f <file>		强制添加
git check-ignore -v <file>	查看生效规则
```

## 配置别名
```sh
git config [--global] alias.<alias> '<original command>'	为所有工作区/当前工作区配置别名
.git/config			当前工作区的配置文件
~/.gitconfig			当前用户的配置文件
```
