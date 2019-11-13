---
title: 导出文件流的excel
date: 2019-11-13 16:12:12
tags:
---
一直以来导出（下载）都是由后端进行创建一个文件地址。然后通过URL进行下载。
最近的项目里，会给后端传送不同的参数，然后后端筛选后以文件流的形式传送给前端。然后再进行导出excel。
不多说，反正自己看，直接上图
![接口返回的参数](导出文件流的excel/1.jpg)
这就是后端返回的数据。
那么，如何导出呢。
因为是在vue中使用的。写法就按照Axios的写法。
```bash
    this.$http.post(url,data,{
        responseType: 'blob'
    }).then(res=>{
        let blob = new Blob([res.data], {
            type: 'application/vnd.ms-excel,application/vnd.openxmlformats-officedocument.spreadsheetml.sheet'
        })
        if (window.navigator.msSaveOrOpenBlob) {
            navigator.msSaveBlob(blob);
        } else {
            let elment = document.createElement('a');
            elment.download = "导出的文件名称.xlsx";
            elment.style.display = 'none';
            elment.href = URL.createObjectURL(blob);
            document.body.appendChild(elment);
            elment.click();
            document.body.removeChild(elment);
        }
    }).catch(err => {
        console.warn(err);
    })
```
这里使用了blob对象，那么blob对象又是什么呢。
Blob(Binary Large Object)术语最初来自数据库（oracle 中也有类似的栏位类型。），早期数据库因为要存储声音、图片、以及可执行程序等二进制数据对象所以给该类对象取名为Blob。 
在Web领域，Blob被定义为包含只读数据的类文件对象。Blob中的数据不一定是js原生数据形式。常见的File接口就继承自Blob，并扩展它用于支持用户系统的本地文件。

构建一个Blob对象通常有三种方式：
1.通过Blob对象的构造函数来构建。
2.从已有的Blob对象调用slice接口切出一个新的Blob对象。
3.canvas API toBlob方法，把当前绘制信息转为一个Blob对象。
在上述代码中使用的就是第一种方法。
```bash
    var blob = new Blob(array[optional], options[optional]);
```
new Blob 可以传入两个参数
第一个为数据序列，可以为任意格式的值。
第二个用于指定将要放入Blob中的数据的类型。

