---
layout: post
tags: nodejs
---

Windows下的NodeJS安装是比较方便的,只需要登陆官网,[http://nodejs.org/](http://nodejs.org/)，便可以看到首页的“INSTALL”按钮，直接点击就会自动下载安装。安装过程基本直接“NEXT”就可以了。（Windows的安装msi文件在过程中会直接添加path的系统变量，变量值是你的安装路径，我这里的演示是安装在`D:\Program Files\nodejs`）安装完成之后，我们先检测下NodeJS是否安装成功，cmd命令行中键入：

```javascript
 > node -v
   v0.12.1

 > npm -v
   2.14.7
```

OK,NodeJS这样就算安装成功了

npm作为一个NodeJS的模块管理，我们要先配置npm的全局模块的存放路径以及cache的路径，例如我希望将以上两个文件夹放在NodeJS的主目录下，便在NodeJs下建立“node_global”及“node_cache”两个文件夹。我们就在cmd中键入两行命令：

```javascript
 > npm config set prefix "D:\Program Files\nodejs\node_global"
```

```javascript
 > npm config set cache "D:\Program Files\nodejs\node_cache"
```

现在我们来装个模块试试，选择bower这个比较常用的模块。同样在cmd命令行里面，输入：

```javascript
 > npm install bower -g
```

*注意：这里“-g”这个参数意思是装到global目录下，也就是上面说设置的“D:\Program Files\nodejs\node_global”里面。待cmd里面的安装过程滚动完成后，会提示“bower”装在了哪、版本还有它的目录结构是怎样。*


下面这一步非常关键，我们需要设置系统变量。进入我的电脑→属性→高级→环境变量。在系统变量下新建“NODE_PATH”，输入“D:\Program Files\nodejs\node_global\node_global”
或者复制路径到变量的`path`

```javascript
 > npm config get prefix
   D:\Program Files\nodejs\node_global
```


参考：[command-not-found-window系统环境变量的问题](http://stackoverflow.com/questions/21732447/bower-command-not-found-windows)


如果以上步骤都OK的话，我们可以再次开启cmd命令行，键入：

```javascript
 > bower -v
   1.4.1
```

OK~~~~