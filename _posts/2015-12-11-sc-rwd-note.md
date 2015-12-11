---
layout: post
title:  国际站自适应布局rwd.js
author: 古月云希
---

阿里巴巴国际站自适应布局使用说明：

### 一、引入css文件

兼容ie8浏览器，注意css引入顺序

```html 
    <!--[if IE 8]>
        <link href="http://style.aliunicorn.com/css/6v/apollo/core/rwd-sc-ie8.css" rel="stylesheet" type="text/css" media="all" />
    <![endif]-->

    <link rel="stylesheet" type="text/css" href="http://style.aliunicorn.com/css/6v/apollo/core/rwd-sc.css" />
```


#### 自适应布局说明：




### 二、引入js

我们使用 js 来判断浏览器窗口的宽度，并且计算当前所处的区间
在不支持 media query 的浏览器中，网页必须依赖 rwd.js 和 响应式 CSS 框架的补丁文件来进行

```js

    // 给html标签加rwd
    var html = document.getElementsByTagName('html')[0];
    if(html.className.indexOf('rwd') === -1){
        html.className += 'rwd';
    }

    seajs.use('js/6v/lib/icbu/rwd/_dev/src/rwd', function (rwd) {

        rwd.onBreakpoint(function (currentClass, previousClass) {
            console.log('== breakpoint change ==',   
              '\n[getRwd]:', rwd.getRwd(), /* 当前响应式区间 */
              '\n[getRwdClass]:', rwd.getRwdClass(), /* 当前响应式区间 css class */
              '\n[isRwd]:', rwd.isRwd, /* 是否通过 < html class="rwd" > 开启响应式监听模式 */
              '\n[isJsHack]:', rwd.isJsHack /* 是否在不支持 media query 的浏览器上开启 js hack 模式，比如 IE8  */
            );
        });
    });
```

加载rwd.js之后，html class的变化

```html 
    <!-- [XS] -->
    <html class="rwd rwd-xs">
    <!-- [XS] in ie8 -->
    <html class="rwd rwd-xs ie-xs">

    <!-- [S] -->
    <html class="rwd rwd-s">
    <!-- [S] in ie8 -->
    <html class="rwd rwd-s ie-xs ie-s">

    <!-- [M] -->
    <html class="rwd rwd-m">
    <!-- [M] in ie8 -->
    <html class="rwd rwd-m ie-xs ie-s ie-m">

    <!-- [L] -->
    <html class="rwd rwd-l">
    <!-- [L] in ie8 -->
    <html class="rwd rwd-l ie-xs ie-s ie-m ie-l">

```


### template 如下

```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>国际站自适应需求文档</title>
        <link rel="stylesheet" type="text/css" href="http://style.aliunicorn.com/css/6v/apollo/core/core-sc.css?v=2014-09-22" />
        <!--[if IE 8]>
            <link href="http://style.aliunicorn.com/css/6v/apollo/core/rwd-sc-ie8.css" rel="stylesheet" type="text/css" media="all" />
        <![endif]-->
        <link rel="stylesheet" type="text/css" href="http://style.aliunicorn.com/css/6v/apollo/core/rwd-sc.css" />
        <script type="text/javascript" src="http://style.aliunicorn.com/js/6v/atom/atom-tms.js?v=2015-04-14"></script>
        <script src="http://style.aliunicorn.com/js/5v/lib/jquery/jquery-1.8.3.min.js?v=2015-04-14"></script>
        <link rel="stylesheet" type="text/css" href="css/style.css" />
        <style type="text/css">
        .rwd .container{ max-width: 100%;}  
        .row{ margin-bottom: 10px; }
        .inner{ text-align: center; height: 60px; line-height: 60px; font-size: 18px; background-color: #eaeaea;}
        </style>
    </head>
    <body>

        <div class="container">
            
            <div class="row">
                <div class="col-xs-60 col-s-30">
                    <div class="inner" style="background-color: #ecb5e9;">col-1</div>
                </div>
                <div class="col-xs-60 col-s-30">
                    <div class="inner" style="background-color: #91fb7c;">col-2</div>
                </div>
            </div>
            <!-- /两列布局 -->
            
            <div class="row">
                <div class="col-xs-60 col-s-20">
                    <div class="inner" style="background-color: #ecb5e9;">col-1</div>
                </div>
                <div class="col-xs-60 col-s-20">
                    <div class="inner" style="background-color: #7ce2fb;">col-2</div>
                </div>
                <div class="col-xs-60 col-s-20">
                    <div class="inner" style="background-color: #fbca7c;">col-3</div>
                </div>
            </div>
            <!-- /三列布局 -->
            
            <div class="row">
                <div class="col-xs-60 col-s-30 col-m-15">
                    <div class="inner"  style="background-color: #ecb5e9;">col-1</div>
                </div>
                <div class="col-xs-60 col-s-30 col-m-15">
                    <div class="inner" style="background-color: #7ce2fb;">col-2</div>
                </div>
                <div class="col-xs-60 col-s-30 col-m-15">
                    <div class="inner"  style="background-color: #fbca7c;">col-3</div>
                </div>
                <div class="col-xs-60 col-s-30 col-m-15">
                    <div class="inner" style="background-color: #eefb7c;">col-4</div>
                </div>          
            </div>
            <!-- /四列布局 -->
        </div>
    </body>

    <script type="text/javascript">

        // 给html标签加rwd
        var html = document.getElementsByTagName('html')[0];
        if(html.className.indexOf('rwd') === -1){
            html.className += 'rwd';
        }

        seajs.use('js/6v/lib/icbu/rwd/_dev/src/rwd', function (rwd) {

            rwd.onBreakpoint(function (currentClass, previousClass) {
                console.log('== breakpoint change ==',   
                  '\n[getRwd]:', rwd.getRwd(), /* 当前响应式区间 */
                  '\n[getRwdClass]:', rwd.getRwdClass(), /* 当前响应式区间 css class */
                  '\n[isRwd]:', rwd.isRwd, /* 是否通过 < html class="rwd" > 开启响应式监听模式 */
                  '\n[isJsHack]:', rwd.isJsHack /* 是否在不支持 media query 的浏览器上开启 js hack 模式，比如 IE8  */
                );
            });
        });
    </script>
    </html>

```