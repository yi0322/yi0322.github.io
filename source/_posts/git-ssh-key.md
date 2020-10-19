---
title: 🔨Git 配置 SSH-KEY
date: 2020-10-18 22:02:27
tags:
---

配置 Github SSH 连接
<!-- more -->

<a name="27812a1d"></a>
## 配置用户信息

这两条配置很重要，每次 Git 提交时都会引用这两条信息，说明是谁提交了更新，所以会随更新内容一起被永久纳入历史记录

```shell
git config --global user.name "你的用户名"
git config --global user.email 你的邮箱
```

<a name="d4b58067"></a>
## 生成 ssh-key

```shell
ssh-keygen -t rsa -C "你的邮箱"
```

<a name="e58528fd"></a>
## 在 github 上添加 ssh-key
