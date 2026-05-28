---
title: GitHub 多账号混用方案总结（SSH + HTTPS）
date: 2026-05-28 22:02:02
categories:
  - Note
tags:
  - git
---

## 一、整体方案说明

### 适用场景

一台设备使用两个 GitHub 账号：

1. 账号 A（个人）：**纯 SSH 方式**，不依赖 GitHub CLI \(gh\)

2. 账号 B（工作 / 其他）：**纯 HTTPS 方式**，由 gh 管理登录与凭据

### 核心优势

- 两套认证完全隔离，不会串账号、权限混乱

- 无需频繁执行账号切换命令，使用简单

- 符合 GitHub 安全规范，不共用 SSH 密钥

## 二、关键前置规则

1. **SSH 限制**

    - 一个 SSH 公钥**仅能绑定一个 GitHub 账号**，无法多账号共用

    - 单账号 + 默认命名密钥，**无需配置 ****`\~/\.ssh/config`**

    - 自定义密钥名 / 多组 SSH 密钥，才需要 `\~/\.ssh/config` 区分

2. **GitHub CLI \(gh\) 规则**

    - `gh` 仅管理 **HTTPS 协议** 的登录态与 Git 凭据，和 SSH 无关

    - 可主动在 gh 中删除 SSH 对应的账号，仅保留 HTTPS 账号，环境更干净

    - 仓库使用协议决定认证方式：SSH 仓库走密钥，HTTPS 仓库走 gh 凭据

<!-- more-->

## 三、分步配置流程

### 1\. 配置 SSH 账号（个人账号，无 config）

#### 1\.1 生成默认名称 SSH 密钥

推荐使用 ed25519 算法（安全性更高）：

```bash
ssh-keygen -t ed25519 -C "你的个人GitHub邮箱"
```

- 全程回车，使用默认路径与文件名：`\~/\.ssh/id\_ed25519`

- 按需设置密钥密码（可选）

#### 1\.2 上传公钥到 GitHub

1. 查看公钥内容：

```bash
cat ~/.ssh/id_ed25519.pub
```

2. 复制全部输出内容

3. 登录个人 GitHub → `Settings` → `SSH and GPG keys` → `New SSH key`

4. 粘贴公钥，保存即可

#### 1\.3 测试连通性

```bash
ssh -T git@github.com
```

出现 `Hi 用户名\! You\&\#39;ve successfully authenticated` 即配置成功。

> 补充：当前为**单 SSH 账号 + 默认密钥**，**删除 / 不创建 ****`\~/\.ssh/config`**** 均可正常使用**。
> 
> 

---

### 2\. 配置 HTTPS 账号（工作账号，gh 管理）

#### 2\.1 登录 gh（仅保留该账号）

```bash
# 交互式登录工作账号，选择 HTTPS 方式，使用个人访问令牌(PAT)认证
gh auth login
```

#### 2\.2 查看当前 gh 登录列表

```bash
gh auth status
```

#### 2\.3 删除 gh 中多余的 SSH 对应账号（关键步骤）

如果列表里存在个人 SSH 账号，执行删除：

```bash
# 替换为你的个人 GitHub 用户名
gh auth logout --user 个人用户名
```

执行后再次 `gh auth status`，确保仅保留**工作账号**。

#### 2\.4 关联 Git 凭据

让 Git 自动复用 gh 的 HTTPS 登录态，免重复输入账号密码：

```bash
gh auth setup-git
```

---

### 3\. 仓库使用规范（核心，避免串账号）

#### 3\.1 个人仓库（SSH 协议）

克隆 / 使用必须使用 SSH 地址，**全程无需操作 gh**

```bash
git clone git@github.com:个人用户名/仓库名.git
# 日常拉取、推送
git pull
git push
```

#### 3\.2 工作仓库（HTTPS 协议）

克隆 / 使用必须使用 HTTPS 地址，gh 保持当前账号即可，无需切换

```bash
git clone https://github.com:工作账号/仓库名.git
# 日常拉取、推送
git pull
git push
```

## 四、常用排查与问题解决

### 1\. 查看仓库当前使用协议

进入仓库目录执行：

```bash
git remote -v
```

- 地址为 `git@github\.com` → SSH 协议，走密钥认证

- 地址为 `https://github\.com` → HTTPS 协议，走 gh 凭据

### 2\. HTTPS 认证异常（凭据缓存冲突）

清除本地 Git 凭据缓存：

```bash
git credential-manager reject https://github.com
```

之后重新执行 `gh auth setup\-git`。

### 3\. 误混用协议导致权限报错

- 个人仓库误用 HTTPS：远程地址改为 SSH 格式

- 工作仓库误用 SSH：远程地址改为 HTTPS 格式
修改远程地址命令示例：

```bash
# 切换为 SSH
git remote set-url origin git@github.com:用户名/仓库名.git
# 切换为 HTTPS
git remote set-url origin https://github.com/用户名/仓库名.git
```

## 五、最终使用总结

1. **SSH 个人账号**

    - 不依赖 gh，gh 中已删除该账号登录态

    - 单默认密钥，无需 `\~/\.ssh/config`

    - 所有操作 `git pull/push` 直接执行，零切换

2. **HTTPS 工作账号**

    - 仅由 gh 管理，gh 常驻该账号即可

    - 无需执行 `gh auth switch` 切换账号

    - 所有 HTTPS 仓库自动复用凭据

3. 整体原则：**协议绑定账号，两套体系完全独立**，是多账号场景下最简、最稳定的混用方案。

---

### 保存说明

1. 全选上方所有文本，复制；

2. 本地新建文本文档，粘贴内容；

3. 将文件后缀名改为 `\.md`（例如 `github\-multi\-account\.md`），即可完成保存下载。

> （注：文档部分内容可能由 AI 生成）
