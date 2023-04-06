---
title: nvm usage
date: 2023-04-06 13:32:43
categories:
  - Manual
tags:
  - nodejs
  - nvm
toc: true
---

```
Usage:
  nvm --help                                显示此消息
  nvm --version                             打印出安装的nvm版本
  nvm install [-s] <version>                从源代码下载并安装 <version>, [-s]。 如果可用，使用 .nvmrc
    --reinstall-packages-from=<version>     安装时，重新安装安装在 <node|iojs|node version number> 中的包
    --lts                                   安装时，只选择 LTS（长期支持）版本
    --lts=<LTS name>                        安装时，仅从特定 LTS 行的版本中选择
    --skip-default-packages                 安装时，跳过默认包文件（如果存在）
    --latest-npm                            安装后，尝试升级到给定节点版本上的最新工作 npm
    --no-progress                           禁用任何下载的进度条
  nvm uninstall <version>                   卸载一个版本
  nvm uninstall --lts                       使用自动 LTS（长期支持）别名“lts/*”（如果可用）进行卸载。
  nvm uninstall --lts=<LTS name>            使用提供的 LTS 行的自动别名（如果可用）进行卸载。
  nvm use [--silent] <version>              修改 PATH 以使用 <version>。 如果可用，使用 .nvmrc
    --lts                                   使用自动 LTS（长期支持）别名“lts/*”（如果可用）。
    --lts=<LTS name>                        为提供的 LTS 行使用自动别名（如果可用）。
  nvm exec [--silent] <version> [<command>] 在 <version> 上运行 <command>。 如果可用，使用 .nvmrc
    --lts                                   使用自动 LTS（长期支持）别名“lts/*”（如果可用）。
    --lts=<LTS name>                        为提供的 LTS 行使用自动别名（如果可用）。
  nvm run [--silent] <version> [<args>]     在 <version> 上以 <args> 作为参数运行 `node`。 如果可用，使用 .nvmrc
    --lts                                   使用自动 LTS（长期支持）别名“lts/*”（如果可用）。
    --lts=<LTS name>                        为提供的 LTS 行使用自动别名（如果可用）。
  nvm current                               显示当前激活的Node版本
  nvm ls [<version>]                        列出已安装的版本，匹配给定的 <version>（如果提供）
    --no-colors                             抑制彩色输出
    --no-alias                              抑制 `nvm alias` 输出
  nvm ls-remote [<version>]                 列出可用于安装的远程版本，匹配给定的 <version>（如果提供）
    --lts                                   列出时，只显示 LTS（长期支持）版本
    --lts=<LTS name>                        列出时，仅显示特定 LTS 行的版本
    --no-colors                             抑制彩色输出
  nvm version <version>                     将给定的描述解析为单个本地版本
  nvm version-remote <version>              将给定的描述解析为单个远程版本
    --lts                                   列出时，仅选择 LTS（长期支持）版本
    --lts=<LTS name>                        列出时，仅从特定 LTS 行的版本中选择
  nvm deactivate                            撤消 `nvm` 对当前 shell 的影响
  nvm alias [<pattern>]                     显示所有以 <pattern> 开头的别名
    --no-colors                             抑制彩色输出
  nvm alias <name> <version>                设置一个名为 <name> 的别名指向 <version>
  nvm unalias <name>                        删除名为 <name> 的别名
  nvm install-latest-npm                    尝试在当前节点版本上升级到最新的工作“npm”
  nvm reinstall-packages <version>          将 <version> 中包含的全局 `npm` 包重新安装到当前版本
  nvm unload                                从 shell 中卸载 `nvm`
  nvm which [current | <version>]           显示已安装节点版本的路径。 如果可用，使用 .nvmrc
  nvm cache dir                             显示 nvm 缓存目录的路径
  nvm cache clear                           为 nvm 清空缓存目录

Example:
  nvm install 8.0.0                     安装特定版本号
  nvm use 8.0                           使用最新的 8.0.x 版本
  nvm run 6.10.3 app.js                 使用节点 6.10.3 运行 app.js
  nvm exec 4.8.3 node app.js            使用指向节点 4.8.3 的路径运行 `node app.js`
  nvm alias default 8.1.0               在 shell 上设置默认节点版本
  nvm alias default node                始终默认为 shell 上的最新可用节点版本

Note:
  to remove, delete, or uninstall nvm - just remove the `$NVM_DIR` folder (usually `~/.nvm`)
  移除、删除或卸载 nvm - 只需移除 `$NVM_DIR` 文件夹（通常为 `~/.nvm`）
```
