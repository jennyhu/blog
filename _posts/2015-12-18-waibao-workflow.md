---
layout: post
title:  各BU工作流程
author: 古月云希
---
淘宝新TMS的各种坑总结

## 一、开发一个模块

开发模块之前，首先需要保证本机已经配置好正确的开发环境。

### 1、初始化模块文件夹 

新建一个工作目录 执行命令

```bash
    //选择你需要进入的BU
    > def tms init 
    //外包同学设置
    > def tms set partner true 
```

### 2、 登陆TMS

与tms交互之前（如 create、schema），需要确保是登陆状态，执行命令行：

```bash
    > def tms login
```

### 3、新建模块

```bash
    > def tms create wb-MODNAME
```

**外包同学的模块名必须以wb-开头，否则无法提交模块**

*参数*

- MODNAME, 模块名称
- -m, --module 创建模块
- -p, --page创建模块（源码页面）

### 4、配置schema数据

```bash
    > def tms schem
```

*参数*

- -f,--flash 同步最新 schema 版本 hash 到模块

**注意：在发布之前需要先配置schema数据，通知tms获取最新的schema的数据结构。**

```bash
    > def tms schem -f
```

### 5、调试开发模块 

```bash
    > def tms dev
```

*参数*

- -m, --module [name] 调试模块
- -p, --page [创建模块] 调试（源码页面）

### 6、开发模块

- 在index.xtpl中开发，用[xtemplate语法](https://github.com/xtemplate/xtemplate/blob/master/docs/syntax-cn.md)编写。
- 样式写在index.less文件中，用[less语法编写](http://jennyhu.github.io/blog/2015/11/26/mixins-less.html)。
- 模块逻辑写在index.js文件中，用[kissy编写](http://docs.kissyui.com/)。
- tms.json文件中编写模块的信息，内容如下 
    * name: 模块名称
    * author: 开发者
    * description： 模块描述，说明模块功能
    * assets: 模块包依赖
    * widths: 适应屏幕宽度
    * schema： schema数据配置项，执行schema命令可自动生成
    * screenshot: 模块缩略图，填写图片路径信息，可在tms模块管理 中通过缩略图查看到该模块

## 二、发布和验收(git命令)

### 1、将本地模块提交到本地版本库：
```bash
    > git add .
    > git commit -m [提交注释]
```

*外包同学因为使用tnpm进行模块创建，所以不需要推送到master，请省略git push origin master的操作*

### 2、创建预发布分支

```bash
    > git checkout -b daily/0.0.1
    > git push origin daily/0.0.1  //输入用户名和密码
```

### 3、创建tag分支并发布到tag分支上（线上）

成功推送到预发后，首先需要创建tag，命名规范为：publish/x.x.x，并将该tag推送 到线上，系统会自动将daily分支删除掉。

```bash
    > git tag publish/0.0.1
    > git push origin publish/0.0.1 //输入用户名和密码
```

*修改模块重新提交重复1、2、3步骤 只需把分支的版本号改一下*


## 三、下载别人的模块

```bash
   > git clone http://tpm.tms.taobao.com/git/repo/tb-mod/MODNAME.git 
   > cd wb-zc-mod-first.git
   > git branch -a //查看所有分支
   > git checkout daily/0.0.HIGHVERSION //切到版本最高的分支
```


## 四、淘宝BU(主要是村淘)


## 五、阿里BU

tms.json:

```javascript
    {
      "name":"wbZcYunxiTest",
      "version":"0.0.1",
      "author": "古月云希",
      "type":"module",
      "group":"ali",
      "description": "description……",
      "template": {
            "type": "xtemplate",
            "ext": ".xtpl",
            "version": "~4.0.5"
      },
      "assets":{
            "kissy":"^1.4.16",
            "tb-global":"*",
            "ali-init":"*"
      },
      "widths": [
            "100%"
      ],
      "schema": {
            "id": "",
            "version": ""
      },
      "screenshot":""
    }

```

abc.json:

```javascript
    {
        "type":"tms",
        "builder":"@ali/builder-tms",
        "author": "古月云希",
        "options": {
            "packageName": "ali-mod"
        },
        "plugins":{

        }
    }
```

## 六、去啊BU

