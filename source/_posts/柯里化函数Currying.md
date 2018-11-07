---
title: 柯里化函数Currying
date: 2018-09-12 10:30:14
tags: JavaScript
---
## 柯里化函数
在计算机科学中，柯里化（英语：Currying），又译为卡瑞化或加里化，是把接受多个参数的函数变换成接受一个单一参数（最初函数的第一个参数）的函数，并且返回接受余下的参数而且返回结果的新函数的技术。这个技术由 Christopher Strachey 以逻辑学家哈斯凯尔·加里命名的，尽管它是 Moses Schönfinkel 和 Gottlob Frege 发明的。 ---wiki(维基百科)

### 例子

实现 add(1)(2)(3)() = 6 的效果
从上看出。要是实现一个function 让其调用的参数相加得出一个数。当入参为0的时候返回这个数
1.传入参数的时候先存储起来。
2.带入参为空的时候运行
``` bash
    function currying(fn){
        var allArgs = []; # 因为allArgs在next内调用，行程闭包。不会被回收。

        return function next(){
            var args = [].slice.call(arguments);

            if(args.length > 0){
                allArgs = allArgs.concat(args);
                return next;
            }else{
                return fn.apply(null, allArgs); 
                # 当arguments.length === 0的时候停止调用了
            }
        } 
    }
    var add = currying(function(){
        var sum = 0;
        for(var i = 0; i < arguments.length; i++){
            sum += arguments[i];
        }
        return sum;
    });

    console.log(add(1)(2)(3)()); # 6
```

### 记录之前遇到的问题
这时候想到之前遇到的一个问题。 如何实现add(1)(2)(3) = 6
看似跟上面没什么区别。区别就在于什么时候执行结束 计算出结果。
``` bash
    var add = function (n) {
        var num = n;
        var addM = function (m) {
            num += m
            return addM
        }
        addM.toString = function () {
            return num
        }
        return addM
    }
    console.log(add(1)(2)(3)(4)) # function 10
```
