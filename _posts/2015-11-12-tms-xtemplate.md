---
layout: post
title:  新版tms之xtemplate语法（四）
author: 古月云希
---

变量会从当前模板的上下文上查找值，如果你想输出一个变量的值，可以使用：



### XTemplate 模板语法


### 变量

变量会从当前模板的上下文上查找值，如果你想输出一个变量的值，可以使用：

> {{"{{ username "}}}}

这样模板引擎将会从上下文上去查找变量 username 然后打印出来。变量可以使用 `. `来访问属性，和 javascript 一样，也可以用 `[]`。

> {{"{{ user.name "}}}} 

> {{"{{ user[name] "}}}} 


如果一个变量的值是 undefined 或者 null，什么也不会被输出。同样的，如果引用了 undefined 或者 null 的属性，也不会输出任何值（也不会报错）。下面的这些操作当 foo === undefined 的时候，都不会输出任何值：{{ foo }}, {{ foo.bar }}, {{ foo.bar.baz }}。

<br/>
### 支持的数据类型

XTemplate 支持 javascript 中所有的基本数据类型。

- string
- number
- boolean
- null
- undefined
- object
- array

<br/>
### 输出

### 参考资料

- [XTemplate 模板语法](https://github.com/xtemplate/xtemplate/blob/master/docs/syntax-cn.md)