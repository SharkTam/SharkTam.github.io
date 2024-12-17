---
layout: post
title: 'Lab1: IntelliJ, Java, git'
date: 2024-12-17 06:16 +0000
description: 
image: 
category: [Java, CS61B]
tags: 
published: true
math: true
---

首先在 `github` 上创建一个私有仓库，名字任意。

### A. Getting the Starter Files

1. 安装 `git`，配置邮箱名和名字：
   ```
   $ git config --global user.email "you@berkeley.edu"
   $ git config --global user.name "Your Name"
   ```
2. 克隆你创建的私有仓库到本地，然后进入该文件夹：
   ```
   $ git clone git@github.com:SharkTam/sp21-CS61B.git
   $ cd sp21-CS61B
   ```
3. Add the `skeleton` remote repository. You will “pull” code from this remote repository to get starter code for assignments. Make sure that you are within the newly created repository folder before you continue with these commands.
   ```
   $ git remote add skeleton https://github.com/Berkeley-CS61B/skeleton-sp21.git
   # 告诉 Git 将一个名为 "skeleton" 的远程仓库添加到你的本地Git项目中。
   # 这个命令并不会拉取或下载任何文件到你的本地项目；它只是设置了一个可以与之通信的远程地址。

   $ git remote -v
   # 用于列出所有已配置的远程仓库及其对应的克隆 URL
   ```
4. You must now “pull” from the `skeleton` remote in order to get the starter code for Lab 1. You will also do this when new projects and assignments are released. To do this, use the spookiest command in the whole git toolbox:
   ```
   $ git pull skeleton master
   # 从远程仓库 skeleton-sp21 中的 master 分支中拉取代码
   ```
   >开了 vpn 还是会出现因为网络问题无法 pull 的情况，需要为 git 配置代理才能拉取，下面是为 http、https 配置代理的方法
   {: .prompt-warning}
   ```
   $ git config --global http.proxy 127.0.0.1:7890
   $ git config --global https.proxy 127.0.0.1:7890
   # 后面的端口号为 vpn 软件中的端口号
   ```
5. If you list the files in your current directory, you’ll see that there is now a folder named `lab1` Look in the `lab1` folder and you’ll see files called `HelloWorld.java`, `HelloNumbers.java`, `Collatz.java`, and others, that you’ll work with in later parts of this lab.

### B. Running Code in IntelliJ

与 snap 相关的内容都不需要配置。（好像只有校内人员才能用）

### D. Programming Exercise

如果 n 为偶数，下一个数位 n/2；如果 n 是奇数下一个数为 3n + 1；如果 n 为 1 数列结束。

### E. Pushing Your Work to GitHub

### F. Submitting Lab 1
