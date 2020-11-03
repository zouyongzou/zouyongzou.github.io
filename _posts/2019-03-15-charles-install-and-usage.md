---
title: "抓包工具 Charles 安装和使用教程"
excerpt: "Charles 是macOS上常用的抓包工具，同时也支持Windows和Linux，用来分析http或者https请求，方便进行调试。"
comments: true
search: true
tags: [工具]
toc: true
toc_sticky: true
---

Charles是macOS上常用的抓包工具，同时也支持Windows和Linux，用来分析http或者https请求，方便进行调试。

### 安装

打开[官网](https://www.charlesproxy.com/)，进入到 **DOWNLOAD** 页，下载对应系统的[安装包](https://www.charlesproxy.com/download/)，安装即可。

charles 为付费软件，没有Licenses只能使用30天，网上找了个Licenses  
Registered Name: https://zhile.io  
License Key: 48891cf209c6d32bf4  
有条件的建议购买License
{: .notice}

### 开始使用

打开Charles，macOS下会弹出授权，同意授权即可；windows在安装过程就已授权，所以不需要再次授权。
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031501.png" alt="" class="align-center">
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031502.png" alt="" class="align-center">

进入菜单 Proxy -> macOS Proxy/windows Proxy ,确保已勾选，浏览器随便打开一个网址，Charles 列表就会展示所有的请求，点击展开就能看到详情；如果点开的是https请求，详情可能会出现乱码或者unknown。
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031509.png" alt="" class="align-center">
这是因为我们没有安装ssl证书，数据无法解析或者是没有设置443端口，所以下一步我们需要安装证书，并设置443端口。

点击菜单 Help -> SSL Proxying -> Install Charles Root Certificate，按步骤添加证书，并且**确认证书处于信任状态**。  
macOS下：
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031503.png" alt="" class="align-center">
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031504.png" alt="" class="align-center">

windows下：
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031505.png" alt="" class="align-center">
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031506.png" alt="" class="align-center">
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031507.png" alt="" class="align-center">
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031508.png" alt="" class="align-center">

点击菜单 Proxy -> SSL Proxying Settings -> SSL Proxying，勾选 Enable SSL Proxying，并在Include一栏添加443端口，保存即可。
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031510.png" alt="" class="align-center">

刷新网址，这时候我们就能看到所有的请求，https请求也能正确的展示了。
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031511.png" alt="" class="align-center">

Charles默认启动两个端口，http代理8888端口，socks代理8889端口，建议修改成更不常用的端口，避免与其它服务冲突，可以在 Proxy -> Proxying Settings 中进行配置。

### 移动端使用

1. 手机和电脑进入同一个局域网（连接同一个Wi-Fi），在手机网络连接中设置代理，代理模式选择**手动**，服务器填写电脑IP，端口为上面的设置的端口号，保存（查看电脑ip可在菜单：Help -> Local IP Address 快速查看）。
保存成功之后，Charles 会弹出提示，是否允许信任IP，点击**Allow**，之后可以在菜单 Proxy -> Access Control Settings 管理已信任的IP。
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031513.png" alt="" class="align-center">
2. 点击菜单 Help -> SSL Proxying，ios 设备选择**Install Charles Root Certificate in ios Simulators**，android 设备选择**Install Charles Root Certificate on a Mobile Device or Remote Browser**。
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031512.png" alt="" class="align-center">
按提示在浏览器输入chls.pro/ssl，会自动下载证书，点击安装证书，并且信任证书，手机上打开网页就能看到请求了。

更多详情内容可以查看[官方文档](https://www.charlesproxy.com/documentation/)
