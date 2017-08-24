---
layout:   post
title:    "艺师汇项目总结（pc 端）"
date:     2016-11-11
excerpt:  实习也有一段时间了，总结一下艺师汇项目中所用的一些技术。
project:  true
tags:     [项目]
comments: true;
---

###### 实习也有一段时间了，总结一下艺师汇项目中所用的一些技术。

##### 1、swiper插件

##### 2、点击图片放大

##### 3、判断客户端为移动端或pc端

{% highlight javascript %}
var isMobile =  navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i)
if (isMobile) {
    console.log('mobile')
} else {
    console.log('pc')
}
{% endhighlight %}

##### 4、姐姐