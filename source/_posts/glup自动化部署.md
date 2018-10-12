---
title: glup自动化部署
date: 2018-10-12 14:13:25
tags: 工具
---
## 前言
最近做了一个项目，一个聊天窗口项目。前端这里技术还是用的vue。之前部署都是在Jenkins上写好shell脚本。然后直接点一下就行。由于这个项目并没有人去配这个。每一次发版都是ssh登录服务器。然后cd到目录下。把本地的文件打包rz上去。再进行unzip。这一通操作，浪费了不少时间。而且还容易出错。由于使用的是root用户。每天在服务器上rm -rf 删掉旧的版本。心惊胆战（删库跑路）。所以准备借用gulp实现自动化上传。
由于cli的脚本已经做了压缩处理。形成了index.html跟static文件夹。就不再使用gulp进行压缩了。只做了上传部分以及删除旧文件。

## 环境
Node npm(yarn)
在这里我使用的yarn,都一样。
## 其他依赖
既然用到了gulp。那么gulp是必然需要的，还有一个是gulp-ssh。
```bash
yarn add gulp gulp-ssh --save
```
## 创建文件
在项目的根目录下创建一个叫做gulpfile.js的文件。
剩下的代码我们要在这个文件内完成。
引入所需要的依赖
```bash
const gulp = require('gulp');
const GulpSSH = require('gulp-ssh');
```
### 配置一些东西
```bash
var config = {
    ssh: {
        host: '192.168.***.***', # 地址
        port: 22, # ssh端口
        username:'root', # 用户
        password:'*******', # 密码
    },
    remoteDir: `/data1/workspace/`, # 部署的路径
    commands: [
        # 删除现有文件   
        `rm -rf /data1/workspace/index.html`,
        `rm -f /data1/workspace/static/`
    ]
}
```
### 连接ssh通道
```bash
# 打开ssh通道
var gulpSSH = new GulpSSH({
    ignoreErrors: false,
    sshConfig: config.ssh
});
```
### 默认任务。注意！这里必须得写，必须得写，必须得写。否则会报错。
```bash
gulp.task('default', ['deployFile'], function() {
    // 将你的默认的任务代码放在这

});
```
### 上传代码
```bash
gulp.task('deployFile',['execSSH'],() => {
    console.log('5s后开始上传文件...');
    setTimeout(()=>{
        console.log('倒计时.....5');
    },1000);
    setTimeout(()=>{
        console.log('倒计时....4');
    },2000);
    setTimeout(()=>{
        console.log('倒计时...3');
    },3000);
    setTimeout(()=>{
        console.log('倒计时..2');
    },4000);
    setTimeout(()=>{
        console.log('倒计时.1');
    },5000);
    setTimeout(function() {
        return gulp
            .src(['./dist/**/*', '!**/node_modules/**'])
            .pipe(gulpSSH.dest(config.remoteDir));
    }, 5000);

});
```
### 删除旧代码
```bash
gulp.task('execSSH', () => {
    console.log('删除服务器上文件...');
    return gulpSSH.shell(config.commands, {
            filePath: 'commands.log'
        })
        .pipe(gulp.dest('logs'));
});
```
服务器默认的port为22,如果有做过修改，可以登录服务器后去查看。文件路径是/etc/ssh/sshd_config。

