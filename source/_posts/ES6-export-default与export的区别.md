---
title: ES6-export default与export的区别
date: 2018-11-07 10:17:57
tags: JavaScript
---
日常写Vue的时候，经常在每一个template下的script内export default。开发模块的时候又会用到export。那么，export default 与export 有什么区别呢。

### export
说道export就不得不说import。模块功能主要以两部分组成，一个是export，一个就是import。export用于规定模块对外接口，import则用于输入其他模块提供功能。

在阮一峰的ECMAScript6入门中说道：
一个模块就是一个独立的文件。该文件内部的所有变量，外部无法获取。如果你希望外部能够读取模块内部的某个变量，就必须使用export关键字输出该变量。

```bash
# demo.js
var a = '1';
var b = '2';
export {a,b};
```
ES6将其视为一个模块，export对外输出三个变量。

那么如何做到用import引用呢。
```bash
# main.js
import { a,b } from './demo.js'
```
import接受一对大括号，里面导出指定模块的变量名。这时候需要注意了，大括号内导出的模块变量名要与模块内对外名称接口相同。
也可以直接
```bash
import 'demo'
```
这样import会直接加载所有的模块。
### export default
由于export需要知道模块内的变量名称或者函数名，这样对于一个新手上手的时候必须得先去阅读文档，才能获得这些。
为了带来方便，直接加载模块，就用到了export default，为模块指定默认输出。
```bash
# demo.js
export default function () {
    
}
# 或者换个写法

funcion a () {};
export default a;
```
使用import加载模块。
# main.js
```bash
import a form './demo.js'
```
上面代码的import命令，可以用任意名称指向demo.js输出的方法，这时就不需要知道原模块输出的函数名。需要注意的是，这时import命令后面，不使用大括号。
所以区别就一目了然了。。。

