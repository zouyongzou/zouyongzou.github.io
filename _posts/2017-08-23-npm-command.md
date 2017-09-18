---
layout:   post
title:    "npm 常用命令"
date:     2016-6-28
excerpt:  npm 常用的一些命令，方便有需要时查看
tags:     [Node]
---

##### 1、npmd的配置信息

```
查看部分配置信息    
$ npm config ls

查看所有配置信息
$ npm config ls -l
```
直接修改配置文件
```
修改用户目录下的.npmrc文件（没有则新建）
```
通过命令修改
```
npm config set 'config' 'config-value'
```
通过追加命令
```
比如–registry=”registry-uri”等命令可选项临时配置。
npm install grunt –registry=http://registry.npm.taobao.org
```

##### 2、npm操作
安装
```
// 全局
$ npm install -g "package name"
// 本地
$ npm install "package name"
// 查看包路径
$ npm root [-g]
```
查看
```
// 搜索依赖包
$ npm search "package name"
// 查看依赖包的package.json信息
$ npm view "package-name"
// 另外我们可以单独查看package.json某个配置。
// 查看包的依赖关系
$ npm view "package name" dependencies
// 查看包的源文件地址
$ npm view "package name" repository.url
// 查看包所依赖的node版本号
$ npm view "package name" engines
// 查看当前项目的本地依赖包，
$ npm list
// 查看全局依赖包，
$ npm list -g
// 查看本地依赖包是否不是最新版
$ npm outdated "package name"
```
卸载
```
// 卸载本地
$ npm uninstall "package name"
// 卸载全局
$ npm uninstall -g "package name"
```
更新
```
// 更新本地
$ npm update "package name"
// 更新全局
$ npm update -g "package name"
```
发布包
```
// 1.注册一个registry帐号，然后根据引导输入帐号、密码和邮箱地址。
$ npm adduser
// 2. 登录registry帐号，登录信息会保存在客户端。
$ npm login
// 3. 发布项目，
$ npm publish
```

（完）