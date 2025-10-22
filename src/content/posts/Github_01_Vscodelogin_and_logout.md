---
title: Vscode&Github-章节01：登录与登出
published: 2025-10-21
description: '通过终端来登录以及登出，方便切换git账号以切换变更提交（后续建议用SSH解决）'
image: ''
tags: ["Vscode","Github","HuiyeStudy"]
category: '学习'
draft: false 
lang: ''
---

虽然说现在还只是一个只会fork的普通玩家
但是因为还是习惯一个账号一个项目这样来，导致每个账号切换的时候都会出现传输的问题
就像是今天，将还在写的笔记的账号，就莫名其妙因为设置的出错，成了售后网站的贡献者
难绷（）

简单的记录一下通过终端退出当前账号的方式在个人博客的话，这样的话方便查找，也方便直接进行问题的归纳。
```yaml
---
1️⃣查询git的配置：git config --list
查询我要的git的配置：
git config user.name
git config user.email
git config --global credential.helper
gh auth status

2️⃣消除凭据并重新登录：
cmdkey /list
cmdkey /delete:git:https://github.com

3️⃣使用GCM登录
git push origin main

4️⃣登录后记得，更改git的邮箱和用户名配置（下方代码要保留双引号）：
git config --global user.name "内容更换为用户名"
git config --global user.email "内容更换为邮箱"


后补的-不清楚，但是留存一下生成密钥的方式，没准以后写SSH的时候会回来翻：
生成密钥对：
ssh-keygen -t rsa -C "邮箱账号"


ssh-keygen -t ed25519 -C "you@example.com"
Start-Service ssh-agent
ssh-add $env:USERPROFILE\.ssh\id_ed25519
Get-Content $env:USERPROFILE\.ssh\id_ed25519.pub | clip
# 把剪贴板内容粘到 GitHub -> Settings -> SSH and GPG keys（添加）
git remote set-url origin git@github.com:Huiyebiji/Huiyebiji.git
git push origin main
---