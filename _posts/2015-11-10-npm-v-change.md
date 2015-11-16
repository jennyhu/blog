---
layout: post
title:  npm版本升级和降级
tags: npm

---

npm版本升级和降级

### 查看当前版本

```git
    > npm -v
     2.14.7
  
    > npm version
    { npm: '2.14.7',
      http_parser: '2.3',
      modules: '14',
      node: '0.12.1',
      openssl: '1.0.1m',
      uv: '1.0.2',
      v8: '3.28.73',
      zlib: '1.2.8' 
    }
```


###  npm安装需要的版本
使用 npm -g install npm@2.9.1 （版本号2.9.1 可以根据已发布的版本随意升级或降级），获取最新版本的npm 文件

```git
    > npm -g install npm@2.9.1
    D:\Program Files\nodejs\node_global\npm -> D:\Program Files\nodejs\node_global\node_modules\npm\bin\npm-cli.js
npm@2.14.7 D:\Program Files\nodejs\node_global\node_modules\npm
   
```

复制你刚才安装的npm下的文件(`D:\Program Files\nodejs\node_global\npm`)到你的 NodeJS安装目录下的 \node_modules\npm 中，覆盖掉原有的全部文件；

再次使用 npm -v （npm version 会更详细些） 查看当前版本，好哒，显示的是2.9.1，已经是最新版本了，这种方法也适用于降级处理。