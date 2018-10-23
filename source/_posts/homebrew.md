---
title: brew常用命令
date: 2017-05-24 13:32:43
tags: brew
---

一般来说如果你追求新版本（不升级不舒服斯基），那么你最常用的操作序列就是这样：

```
brew update          # 更新 Homebrew 的信息
brew outdated        # 看一下哪些软件可以升级
brew upgrade <xxx>   # 如果不是所有的都要升级，那就这样升级指定的

brew upgrade; brew cleanup    # 如果都要升级，直接升级完然后清理干净
```

<!--more-->

#### 搜索
`brew search MySQL`

#### 查询
`brew info mysql` 主要看具体的信息，比如目前的版本，依赖，安装后注意事项等

#### 更新
`brew update` 这会更新 Homebrew 自己，并且使得接下来的两个操作有意义

#### 检查过时（是否有新版本）
`brew outdated` 这回列出所有安装的软件里可以升级的那些

#### 升级
`brew upgrade` 升级所有可以升级的软件们

#### 清理
`brew cleanup` 清理不需要的版本极其安装包缓存