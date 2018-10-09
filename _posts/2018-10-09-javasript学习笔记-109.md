---
layout: post
title: javasript学习笔记-10/9
date: 2018-10-09
tags: javascript
---

#### 1.Ajax的工作原理

（1）创建Ajax对象：var xhr = new XMLHttpRequest();

（2）xhr 发送请求：xhr.open('get','test.html','true');

​                          xhr.send();

（3）xhr获取响应：

```javascript
xhr.onreadystatechange = function(){

       if(xhr.readystate == 4){//请求的状态码

              /*

              0:请求还没有建立（open执行前）

              1：请求建立了还没发送（执行了open）

              2：请求正式发送（执行了send）

              3：请求已受理，有部分数据可以用，但还没有处理完成

              4：请求完全处理完成

              */

              alert(xhr.responseText);//返回的数据

        }

}

```



#### 2.运算符号对于变量的转换规则

* 运算中，+号，数字隐式转换成字符串。其余的运算符号是字符串隐式转换成数字。 
* +是一元运算符，相当于我们说的正负，无运算效果，但是可以将字符串等转为number类型。 

#### 3.JavaScript中的全局函数

| 函数                                                         | 描述                                               |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [decodeURI()](http://www.runoob.com/jsref/jsref-decodeuri.html) | 解码某个编码的 URI。                               |
| [decodeURIComponent()](http://www.runoob.com/jsref/jsref-decodeuricomponent.html) | 解码一个编码的 URI 组件。                          |
| [encodeURI()](http://www.runoob.com/jsref/jsref-encodeuri.html) | 把字符串编码为 URI。                               |
| [encodeURIComponent()](http://www.runoob.com/jsref/jsref-encodeuricomponent.html) | 把字符串编码为 URI 组件。                          |
| [escape()](http://www.runoob.com/jsref/jsref-escape.html)    | 对字符串进行编码。                                 |
| [eval()](http://www.runoob.com/jsref/jsref-eval.html)        | 计算 JavaScript 字符串，并把它作为脚本代码来执行。 |
| [isFinite()](http://www.runoob.com/jsref/jsref-isfinite.html) | 检查某个值是否为有穷大的数。                       |
| [isNaN()](http://www.runoob.com/jsref/jsref-isnan.html)      | 检查某个值是否是数字。                             |
| [Number()](http://www.runoob.com/jsref/jsref-number.html)    | 把对象的值转换为数字。                             |
| [parseFloat()](http://www.runoob.com/jsref/jsref-parsefloat.html) | 解析一个字符串并返回一个浮点数。                   |
| [parseInt()](http://www.runoob.com/jsref/jsref-parseint.html) | 解析一个字符串并返回一个整数。                     |
| [String()](http://www.runoob.com/jsref/jsref-string.html)    | 把对象的值转换为字符串。                           |
| [unescape()](http://www.runoob.com/jsref/jsref-unescape.html) | 对由 escape() 编码的字符串进行解码。               |

#### 4.JavaScript的数据类型

* 内置类型（Built-in）Null Undefined Boolean Number String Object Symbol    7种
* 原始类型（Primitives）Null Undefined Boolean Number String Symbol  6种