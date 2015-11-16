---
layout: post
title:  新版tms之xtemplate语法（四）
author: 古月云希
---


{%raw%}

变量会从当前模板的上下文上查找值，如果你想输出一个变量的值，可以使用：



## XTemplate 模板语法


### 变量



变量会从当前模板的上下文上查找值，如果你想输出一个变量的值，可以使用：

> {{ username }}

这样模板引擎将会从上下文上去查找变量 username 然后打印出来。变量可以使用 `. `来访问属性，和 javascript 一样，也可以用 `[]`。



> {{ user.name }} 

> {{ user[name] }} 



如果一个变量的值是 undefined 或者 null，什么也不会被输出。同样的，如果引用了 undefined 或者 null 的属性，也不会输出任何值（也不会报错）。下面的这些操作当 foo === undefined 的时候，都不会输出任何值：{{ foo }}, {{ foo.bar }}, {{ foo.bar.baz }}。

### 支持的数据类型

XTemplate 支持 javascript 中所有的基本数据类型。

- string
- number
- boolean
- null
- undefined
- object
- array

### 输出

使用 `{{ foo }}` 来输出 escape 之后的数据,` {{{ foo }}}` 来输出 unescape 的原始数据。

使用数据 `{ foo: "<script>" }` 渲染这个模板，将会得到下面的结果：
> escape:  \&lt;script \&gt;

> unescape:\<script>


如果你希望输出最原始的数据（包括 `{{}}`），你需要使用 `{{% %}}`语法：


```html
    {{%

    {{x}}

    %}}
```


如果想要给模板增加一些注释，请使用 `{{! comment }}`：




### 一个例子

```html
    <div class="module-wrap J_tb_lazyload">
        <div class="inner">
            <div class="list">
                {{#each(list)}}
                <div class="item {{# if (moduleinfo.isFiveOneRow) }}sitem{{/ if}}">
                        <div class="pic">
                            <a href="{{item_url}}" target="_blank">
                                <img src="{{item_pic}}_290x290.jpg" />
                            </a>
                        </div>
                        <div class="title">
                            <a href="{{item_url}}"  target="_blank">{{ item_title }}</a>
                        </div>
                        <div class="acp"><em>&yen;</em>{{item_price}}</div>
                        <a href="{{item_url}}" class="btn" target="_blank">立即购买</a>
                </div>
                {{/each}}
            </div>
        </div> 
    </div>
```


### 参考资料

- [XTemplate 模板语法](https://github.com/xtemplate/xtemplate/blob/master/docs/syntax-cn.md)


{%endraw%}
