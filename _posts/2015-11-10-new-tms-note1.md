---
layout: post
title:  新版tms之工作环境（一）
author: 古月云希
---


## 开发环境的准备

### 1.git的下载与安装

首先在本机上安装git：git的安装分为OSX、Windows、Linux 三个版本。进入到下载页面，根据本机操作系统，选择相应版本git进行安装：[https://git-scm.com/downloads](https://git-scm.com/downloads)

### 2. 安装node（0.12.x）与npm

安装好git之后，需要验证当前计算机上是否安装好node与npm。`(我的node版本是v0.12.1,npm版本是2.14.7 测试可用)`
*注意*：npm是Node.js默认的模块管理器，不需要单独安装。在安装node的时候，会连带一起安装npm。了解更多关于npm的文档->[请点击这里](http://javascript.ruanyifeng.com/nodejs/npm.html#toc2)

### 3.配置tnpm

#### 1.安装tnpm代理

```javascript
  $ npm install tnpmx -g --registry=http://registry.npm.taobao.org
```

#### 2.安装本地工具

`安装新版def`

```javascript
  $ tnpm install @ali/def -g
  $ def plugin config npm_registry_url http://tpm.tms.taobao.com/registry
```

`安装def-tms`

```javascript
  $ def install @ali/def-tms
```


查看安装好的def-tms信息

```javascript
$ def help tms

  Usage: tms [options] [command]

  Commands:

    init                   初始化workspace
    create [options] <name> 创建 模块/源码页面
    get [options] <name>   获取 模块/源码页面
    schema [options]       schema编辑
    search [options] <keyword> 查找 远程模块/源码页面
    set <key> <val>        设置配置信息
    getc <key>             设置配置信息
    dev [options]          预览调试
    info                   sdk信息查看
    login [options]        登录系统
    update                 更新kimi.json

  Options:

    -h, --help  output usage information

```

#### 3.使用

新建空白文件夹,设置为TMS工作目录(workspace),并且设置合作模式

```javascript
  $ def tms init
  $ def tms set partner true // 外包同学设置
```

**登陆tms——login** 

与tms进行交互之前，例如create、schema，需要先登陆tms:`注意：这里会要求输入域账户密码`

```javascript
  $ def tms login
```


**新建模块——create**

```javascript
  $ def tms creat <name>
```

*参数*

- name,模块名
- -m,--module创建模块
- -p,--page创建模板（源码页面）

<br/>

**编辑模块schema——schema**

需要编辑schema数据的模块，在该模块下执行命令：

```javascript
  $ def tms schema
```

*参数*

- -f,--flash 同步最新schema版本hash到模块

<br/>

**调试本地模块——dev**

调试本地模块、模板，执行命令，可弹出本地调试页面，进行模块调试：

```javascript
  $ def tms dev
```

*参数*

- -m,--module[name]调试模块
- -p,--page[创建模板]调试(源码页面)

<br/>

### 4、参考 

- [安装TNPMX](https://www.npmjs.com/package/tnpmx)
- [开发文档](http://tms-book.alibaba.net/dev_manual/config.html)
- [推荐博客](http://lingyu.wang/#/list?page=2)



