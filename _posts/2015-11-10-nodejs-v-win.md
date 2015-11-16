---
layout: post
title:  windows下管理多个版本nodejs
tags: nodejs GNVM
---


工作中我们可能需要用到一些工具，但这些工具依赖不同版本的node环境，那我们需要来为的切换node的环境吗， window msi安装的用户需要卸载重装的循环吗？ 一切都变得很好，只是因为有了GNVM

### what is GNVM

Node.js version manager on Windows by GO (一个windows上用Go语言实现的node版本管理工具)


### 怎么样获取

git用户

```git
    git clone git@github.com:Kenshin/gnvm-bin.git
```


### 怎么安装

安装过node且已加入环境变量 把下载下来的gnvm.exe放到node.exe所在的目录下

没有安装过node 把gnvm.exe放到自定义的一个目录下，并把这个目录添加到环境变量path中
然后打开命令行，运行gnvm version输出Current version x.x.x则表示安装成功

```git
    $ gnvm version
    Current version 0.1.3
    Copyright (C) 2014 Kenshin Wang <kenshin@ksria.com>
    See https://github.com/kenshin/gnvm for more information.
```

*note:通过图形界面设置的环境变量需要在确定并关掉环境变量设置窗口后打开的cmd中才会生效。*


### 使用gnvm安装node

gnvm的命令集

```git
    Usage:
      gnvm
      gnvm [command]

    Available Commands:
      version                   :: 输出当前gnvm的版本
      install                   :: 安装指定版本的nodejs
      uninstall                 :: 卸载指定版本的nodejs
      use                       :: 切换使用已安装的指定版本的nodejs
      update                    :: Update latest node.exe
      ls                        :: 显示所有已安装的nodejs版本
      node-version              :: 显示<global> <latest>的nodejs版本
      config                    :: Setter and getter registry
      help [command]            :: Help about any command
```

安装前可能要做一些资源源的配置

```git
    > gnvm config INIT 
      Config file C:\Program Files\nodejs\\.gnvmrc init success.
```

```git
    > gnvm config registry http://dist.u.qiniudn.com
      Set success, registry new value is http://dist.u.qiniudn.com/
```

```git
    > gnvm update latest
    > gnvm ls
    > gnvm node-version
      Node.exe latest version is 0.12.2.
      Node.exe global version is 0.10.25.
```

`global` 当前node.exe版本 == node -v. 

`latest` 已安装的可用node.exe 版本，可通过gnvm use x.x.x切换成global.

```git
    > gnvm install 0.11.1 
```

批量安装多个nodejs版本

```git
    > gnvm install 0.11.1 0.11.2 0.11.3
```

通过`use` 使用指定nodejs版本

```git
    > gnvm use 0.11.1 
```

卸载指定`node`版本

```git
    > gnvm uninstall 0.11.1 
```


好使用gnvm use x.x.x切换版本

我们可以愉快的安装和使用依赖各种nodejs版本的工具或库了


## 参考链接

* [gnvm官网: http://ksria.com/gnvm/](http://ksria.com/gnvm/)
* [gnvm github: https://github.com/kenshin/gnvm](https://github.com/kenshin/gnvm)