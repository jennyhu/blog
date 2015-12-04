---
layout: post
title:  less教程
author: 古月云希
---

LESS一种动态样式语言，LESS 将 CSS 赋予了动态语言的特性，如 变量， 继承， 运算， 函数. LESS 既可以在 客户端 上运行 (支持IE 6+, Webkit, Firefox)，也可以借助Node.js或者Rhino在服务端运行。


## 语法

### 一、变量

变量允许我们单独定义一系列通用的样式，然后在需要的时候去调用。所以在做全局样式调整的时候我们可能只需要修改几行代码就可以了。

```css
    /*less*/
    @color:#333;
    #header{
        color: @color;
    }

    /*生成css*/
    #header{
        color:#333;
    }
```

<br/>

### 二、混合

混合可以将一个定义好的class A轻松的引入到另一个class B中，从而简单实现class B继承class A中的所有属性。我们还可以带参数地调用，就像使用函数一样。


(1)、不带参数混合:

```css

    /*不带参数混合less*/
    .bordered {
        border-top: dotted 1px black;
        border-bottom: solid 2px black;
    }

    #menu a {
        color: #111;
        .bordered;
    }

    /*生成css*/
    #menu a {
        color: #111;
        border-top: dotted 1px black;
        border-bottom: solid 2px black;
    }

```

(2)、带参数混合:

```css
    /*带参数混合less*/
    .rounded-corners (@radius: 5px) {  /*默认为5px*/
        border-radius: @radius;
        -webkit-border-radius: @radius;
        -moz-border-radius: @radius;
    }

    #header{
        .rounded-corners;
    }

    #footer{
        .rounded-corners(10px); /*10px*/
    }

    /*生成css*/
    #header{
        border-radius: 5px;
        -webkit-border-radius: 5px;
        -moz-border-radius: 5px;
    }

    #footer{
        border-radius: 10px;
        -webkit-border-radius: 10px;
        -moz-border-radius: 10px;
    }
```

(3)、你也可以定义不带参数属性集合,如果你想隐藏这个属性集合，不让它暴露到CSS中去，但是你还想在其他的属性集合中引用，你会发现这个方法非常的好用:

```css
    /*less*/
    .wrap(){
        text-wrap: wrap;
        white-space: pre-wrap;
        white-space: -moz-pre-wrap;
        word-wrap: break-word;
    }

    pre{
        .wrap;
    }

    /*生成css*/
    pre{
        text-wrap: wrap;
        white-space: pre-wrap;
        white-space: -moz-pre-wrap;
        word-wrap: break-word;
    }
```

<br/>
### 三、嵌套规则

我们可以在一个选择器中嵌套另一个选择器来实现继承，这样很大程度减少了代码量，并且代码看起来更加的清晰。

*注意 & 符号的使用—如果你想写串联选择器，而不是写后代选择器，就可以用到 ` &  `了. 这点对伪类尤其有用如 :hover 和 :focus.*

```css
    /*less*/
    #header {
        h1 {
            font-size: 26px;
            font-weight: bold;
            &.title{
                color:#f00;
            }
        }
        p { font-size: 12px;
            a { 
                text-decoration: none;
                &:hover { 
                    border-width: 1px;
                 }
            }
        }
    }

    /*生成css*/
    #header h1 {
        font-size: 26px;
        font-weight: bold;
    }

    #header h1.title{ color:#f00; }
    #header p { font-size: 12px; }
    #header p a { text-decoration: none; }
    #header p a:hover { border-width: 1px; }
      
```

<br/>

### 四、函数 & 运算

运算提供了加，减，乘，除操作；我们可以做属性值和颜色的运算，这样就可以实现属性值之间的复杂关系。LESS中的函数一一映射了JavaScript代码，如果你愿意的话可以操作属性值。

```css
    /*less*/
    @the-border: 1px;
    @base-color: #111;
    @red:        #842210;

    #header {
        color: @base-color * 3;
        border-left-width: @the-border;
        border-right-width: @the-border * 2;
    }

    #footer { 
        color: @base-color + #003300;
        border-color: desaturate(@red, 10%);
    }

    /*生成css*/
    #header {
        color: #333;
        border-left-width: 1px;
        border-right-width: 2px;
    }
    #footer { 
        color: #114411;
        border-color: #7d2717;
    }

```
<br/>


### Color函数
LESS 提供了一系列的颜色运算函数. 颜色会先被转化成 HSL 色彩空间, 然后在通道级别操作:

```css

    @color:#333;

    .c1{ lighten(@color, 20%); /*颜色变浅20%*/ }
    .c2{ darken(@color, 20%); /*颜色加深20%*/ }

    /*改变颜色饱和度*/
    .c3{ saturate(@color, 20%); /*颜色加色20%*/ }
    .c4{ desaturate(@color, 20%);/*颜色去色20%*/ }

    .c5{ fadein(@color, 10%); }
    .c6{ fadeout(@color, 10%); }
    .c7{ fade(@color, 50%); }

    .c8{ spin(@color, 10); }
    .c9{ spin(@color, -10); }

    .c10{ mix(@color1, @color2);}

```


### Math 函数

```css
    round(1.67); /*returns `2`*/
    ceil(2.4);   /* returns `3`*/
    floor(2.6);  /* returns `2`*/

    percentage(0.5); /* returns `50%`*/
```


### 注释:

```css
    //  不保留注释
    /**/ 保留注释
```
<br/>

### Importing:

你可以在main文件中通过下面的形势引入 .less 文件, .less 后缀可带可不带:

```css
    @import: 'minixs.less';
    @import: 'minixs';
```

如果你想导入一个CSS文件而且不想LESS对它进行处理，只需要使用.css后缀就可以: 这样LESS就会跳过它不去处理它.

```css
    @import: 'reset.css'; /*不建议使用*/
```
<br/>

### 字符串插值:

变量可以用类似ruby和php的方式嵌入到字符串中，像`@{name}`这样的结构:

```css

    @base-url: "http://assets.fnord.com";

    div{
        background-image: url("@{base-url}/images/bg.png");
    }

    /*生成css*/
    div{
        background-image:url("http://assets.fnord.com/images/bg.png");
    }
```
<br/>

### 避免编译
时候我们需要输出一些不正确的CSS语法或者使用一些 LESS不认识的专有语法.
要输出这样的值我们可以在字符串前加上一个 `~`, 例如:

```css
    div {
      filter: ~"ms:alwaysHasItsOwnSyntax.For.Stuff()";
    }

    /*生成css*/
    div {
      filter: ms:alwaysHasItsOwnSyntax.For.Stuff();
    }
```
