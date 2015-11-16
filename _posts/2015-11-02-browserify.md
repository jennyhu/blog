---
layout: post
title:   Browserify跑在浏览器上的Node程序
tags: Browserify
---

Browserify的出现可以让Nodejs模块跑在浏览器中，用require()的语法格式来组织前端的代码，加载npm的模块。在浏览器中，调用browserify编译后的代码，同样写在script标签中


#  Browserify跑在浏览器上的Node程序

1. Browserify介绍
2. Browserify安装
3. Browserify命令行参数
4. 在浏览器中运行Nodejs程序
5. 在浏览器中模块化调用Nodejs程序


## Browserify介绍

Browserify的出现可以让Nodejs模块跑在浏览器中，用require()的语法格式来组织前端的代码，加载npm的模块。在浏览器中，调用browserify编译后的代码，同样写在script标签中。

用 Browserify 的操作，分为3个步骤。

- 写node程序或者模块
- 用Browserify预编译成bundle.js
- 在HTML页面中加载bundle.js


## Browserify安装

> npm install browserify -g


```javascript

    var gulp = require('gulp');
    var myth = require('gulp-myth');
    
```