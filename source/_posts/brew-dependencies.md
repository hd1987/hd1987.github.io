---
title: homebrew依赖关系
date: 2023-04-07 13:32:43
categories:
  - Manual
tags:
  - brew
---

```
Basics:
  brew ls                                           列出所有已安装的包
  brew leaves                                       列出不依赖于另一个已安装包的已安装包
  brew deps --installed --tree                      显示所有包的依赖关系
  brew deps <package>                               显示<package>的依赖包
  brew uses <package> --installed                   显示<package>被哪些包依赖
  brew info <package>                               显示<package的信息

  brew uninstall <package>                          卸载<package>
  brew autoremove                                   移除所有未使用的依赖项

brew-graph:
  brew tap martido/homebrew-graph                   安装brew-graph
  brew install graphviz                             安装graphviz
  brew graph --installed | dot -Tpng -ograph.png    dot格式
  brew graph --installed | fdp -Tpng -ograph.png    fdp格式

    --highlight-leaves
    --reduce
```
