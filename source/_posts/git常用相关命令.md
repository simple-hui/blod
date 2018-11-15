---
title: git常用相关命令
date: 2018-11-15 10:42:19
tags: 工具
---
日常工作中，使用git提交代码，打分支。用到很多git的命令。生怕哪天记混了，所以今天在这里总结一下git的命令。

### clone
克隆git地址上的项目
首先先选取目录，cd到一个文件夹下。然后运行
```bash
git clone path
```
按照提示输入账号密码就可以了。
### add
将修改的文件添加到缓存区
```bash
git add filePath
git add . # 表示添加当前目录下所有的文件
```
### commit
将改动内容添加到HEAD。
```bash
git commit -m '备注信息'
```
只是添加到HEAD,但是并没有推送到远端上。

### push
push 用于提交到远端仓库
```bash
git push origin master
```
master表示远端分支的名称。可以换成任意你想提交到的分支名。

### 常用命令
#### git status
```bash
git status
```
用于查询当前状态
#### git diff
```bash
git diff
```
此命令比较的是工作目录中当前文件和暂存区域快照之间的差异,也就是修改之后还没有暂存起来的变化内容
#### git reset
```bash
git reset master filename
```
这个命令用来把不小心add进去的文件从staged状态取出来,可以单独针对某一个文件操作。
#### git branch
```bash
git branch
```
可以用来列出分支,创建分支和删除分支.
```bash
git branch -v
```
可以看见每一个分支的最后一次提交.
```bash
git branch
```
列出本地所有分支,当前分支会被星号标示出.
```bash
git branch (branchname)
```
创建一个新的分支(当你用这种方式创建分支的时候,分支是基于你的上一次提交建立的). 
```bash
git branch -d (branchname)
```
删除一个分支.

删除remote的分支:
```bash
git push (remote-name) :(branch-name): delete a remote branch.
```
这个是因为完整的命令形式是:
```bash
git push remote-name local-branch:remote-branch
```
而这里local-branch的部分为空,就意味着删除了remote-branch
#### git checkout
```bash
git checkout (branchname)
```
切换到一个分支.
```bash
git checkout -b (branchname)
```
创建并切换到新的分支.

这个命令是将git branch newbranch和git checkout newbranch合在一起的结果.
checkout还有另一个作用:替换本地改动:
```bash
git checkout --<filename>
```
此命令会使用HEAD中的最新内容替换掉你的工作目录中的文件.已添加到暂存区的改动以及新文件都不会受到影响.
注意:git checkout filename会删除该文件中所有没有暂存和提交的改动,这个操作是不可逆的.
#### git merge
```bash
git merge
```
把一个分支merge进当前的分支.
```bash
git merge [alias]/[branch]
```
把远程分支merge到当前分支.
如果出现冲突,需要手动修改,可以用git mergetool.
解决冲突的时候可以用到git diff,解决完之后用git add添加,即表示冲突已经被resolved.

以上是整理的常用的一些命令，有用到再继续补充。












