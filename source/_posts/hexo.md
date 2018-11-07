---
title: Hexo && Git Page 我的个人博客
date: 2018-09-02 09:18:02
tags: 工具
---
博客。应该是程序员都有的一个东西。不仅仅只是供其他人去观看。也可以记录自己所学，所用，所遇到的问题以及解决方案。《论语》温故而知新。所以搭建一个博客用于自己记录也是一件蛮好的事情。

下面记录一下这一次使用Hexo 以及 Git Page搭建博客的过程。
## 系统环境
### 安装Node
要使用Hexo,需要安装Node,如果电脑里还没有安装Node,那就先安装Node吧。[Node.js中文网](http://nodejs.cn/)

### 安装Git
[git下载地址](http://git-scm.com/download/)

### 安装Hexo
``` bash
$ cd d:/hexo
$ npm install hexo-cli -g #在这里使用npm 如果未翻墙 请使用cnpm
$ hexo init blog
$ cd blog
$ npm install
$ hexo g # 或者hexo generate
$ hexo s # 或者hexo server，可以在http://localhost:4000/ 查看
```
在这里 对于一些命令进行记录说明
1.生成静态文件。会在根目录下生成public文件
``` bash
$ hexo generate
```
2.本地启动。
``` bash
$ hexo server
```
3.部署到远端。比如下面要说的GitPage上
``` bash
$ hexo deploy
```
4.新建文章
``` bash
$ hexo new "文章名称" #创建文章
```
5.新建页面
``` bash
$ hexo new page "页面名称" #创建页面
```
## Hexo更换主题
### 安装主题
``` bash
$ hexo clean
$ npm i hexo-generator-json-content --save && npm i --save hexo-wordcount && git clone https://github.com/fi3ework/hexo-theme-archer.git themes/archer --depth=1
```
目前我使用的是一个叫做archer的主题。[传送门](https://github.com/fi3ework/hexo-theme-archer)。这里面有对主题的修改说明。大致看了一下。是用ejs模板做的。可以自己再进行二次开发。

### 启用主题
我们需要在根目录下找到_config.yml文件。文件内有个theme属性，将其设置为archer。

### 运行主题
``` bash
$ hexo g
$ hexo s #访问localhost:4000 就可以看到新的主题了
```
## Git Page部署与设置
### 首先需要明白所谓部署到github的原理。
1.之前步骤中在Github上创建的那个特别的仓库（simple-hui.github.io）一个最大的特点就是其master中的html静态文件，可以通过链接[http://simple-hui.github.io](http://simple-hui.github.io)来直接访问。
2.Hexo -g 会生成一个静态网站（第一次会生成一个public目录），这个静态文件可以直接访问。
3.需要将hexo生成的静态网站，提交(git commit)到github上。
### 使用hexo deploy部署
1.安装hexo-deployer-git
``` bash
$ npm install hexo-deployer-git --save
```
2.在hexo根目录下的_config.yml文件中修改deploy配置
``` bash
deploy:
  type: git
  repo: git@github.com:simple-hui/simple-hui.github.io.git
  branch: master
```
3.执行部署命令
``` bash
$ hexo d
```

做一个自己的博客就完成了。这时候就可以去通过访问[http://simple-hui.github.io](http://simple-hui.github.io)去访问自己的博客啦。

