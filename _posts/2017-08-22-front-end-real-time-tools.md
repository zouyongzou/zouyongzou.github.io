---
title:    "前端实时可视化开发工具"
date:     2016-6-6
excerpt:  介绍4种前端实时可视化开发工具，在开发过程不用手动刷新浏览器，修改代码后，立即体现效果，极大的提高前端开发效率
tags:     [Web]
comments: true
---

介绍4种前端实时可视化开发工具，在开发过程不用手动刷新浏览器，修改代码后，立即体现效果，极大的提高前端开发效率
## 1、livestyle
安装简便，只需下载chrome扩展——livestyle 以及 sublimeText 中 livestyle 包即可，只支持这两者绑定。并且只监听 css 文件的变化。

## 2、livereload
支持 Safari、Chrome 和 Firefox 三个浏览器的扩展,
安装方法与 livestyle 类似。本质为按 F5。

## 3、browsersync
安装
```bash
$ npm install -g browser-sync
```
结合 gulp 和 grunt 构建工具来使用
```bash
$ npm install --save-dev browser-sync
```
安装完成后，在开发文件夹下运行以下命名
```bash
# --files路径是相对于运行该命令的项目（目录）
$ browser-sync start --server --files "css/*.css,*.html"
# 如果你的文件层级比较深，您可以考虑使用**（表示任意目录）匹配，任意目录下任意.css或.html文件。
$ browser-sync start --server --files "**/*.css,**/*.html"
```
## 4、puer（常用）
使用 npm 全局安装 puer 命令
```bash
$ npm install puer -g
```
安装完成后，只需在开发文件输入
```bash
$ puer
```
puer 会默认打开 http://localhost:8000 页面(端口可以`-p`参数进行控制)，并贴心的帮你列出了所有你本地可用的ip以及当前的地址二维码，方便手机访问。
