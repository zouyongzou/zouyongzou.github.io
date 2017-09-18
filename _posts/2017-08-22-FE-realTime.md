---
layout:   post
title:    "前端实时可视化开发工具"
date:     2016-6-6
excerpt:  介绍4种前端实时可视化开发工具，在开发过程不用手动刷新浏览器，修改代码后，立即体现效果，极大的提高前端开发效率
tags:     [前端]
comments: true;
---

###### 介绍4种前端实时可视化开发工具，在开发过程不用手动刷新浏览器，修改代码后，立即体现效果，极大的提高前端开发效率
##### 1、livestyle
安装简便，只需下载chrome扩展——livestyle以及sublimeText中livestyle包即可，只支持这两者绑定。并且只监听css文件的变化。

##### 2、livereload
支持 Safari、Chrome 和 Firefox 三个浏览器的扩展,
安装方法与livestyle类似。本质为按F5。

##### 3、browsersync
安装
```
$ npm install -g browser-sync
```
结合gulp和grunt构建工具来使用
```
$ npm install --save-dev browser-sync
```
安装完成后，在开发文件夹下运行以下命名
```
//--files路径是相对于运行该命令的项目（目录）
$ browser-sync start --server --files "css/*.css,*.html"
//如果你的文件层级比较深，您可以考虑使用**（表示任意目录）匹配，任意目录下任意.css或.html文件。
$ browser-sync start --server --files "**/*.css,**/*.html"
```
##### 4、puer（常用）
使用npm全局安装puer命令
```
$ npm install puer -g
```
安装完成后，只需在开发文件输入
~~~
$ puer
~~~
puer会默认为你打开http://localhost:8000页面(端口可以 -p 8001参数进行控制)，并贴心的帮你列出了所有你本地可用的ip以及当前的地址二维码，方便手机访问。

（完）