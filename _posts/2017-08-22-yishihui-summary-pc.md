---
layout:   post
title:    "艺师汇项目总结（pc 端）"
date:     2016-11-11
excerpt:  实习也有一段时间了，总结一下艺师汇项目中所用的一些技术。
project:  true
tags:     [项目]
comments: true;
---

##### 实习也有一段时间了，总结一下艺师汇项目中所用的一些技术。
[项目地址](https://www.yishihui.com)

#### 1、swiper插件

项目中用到轮播图的地方很多，以前自己开发一个jq 轮播小插件，但不太适用（😅）。所以公司同事推荐了Swiper。  
Swiper 是一个开源、免费、强大的**移动端**触摸滑动插件（PC也是能用的）。官网地址点[这里](http://www.swiper.com.cn/)。
Swiper使用简单，文档也很友好，并且还有一揽子强大的参数，基本能实现项目的需求。Swiper 样式文件为 swiper.min.css，可以找到要修改的样式名进行覆盖，不建议修改源码（在本项目中，因为后续需要多次使用，修改了源码的部分样式）

#### 2、点击图片放大

虽然Swiper实现很好的轮播效果，但并没有提供点击图片放大的功能，所以在Swiper的基础上增加了图片放大功能。  
首先给轮播元素增加样式，改变鼠标的样式，让用户知道图片可以点击放大。
{% highlight css %}
// css
.swiper-slide {
    cursor: url(zoom-in.cur), pointer;
}
{% endhighlight %}
目前cursor可以取值zoom-in/zoom-out，但官方建议尽量不要在生产环境中使用。具体详情访问[MDN](https://developer.mozilla.org/zh-CN/docs/Web/CSS/cursor)。
接着获取所有图片的url存入数组，插入自定义的html结构中。增加左右切换按钮，关闭按钮即可。

#### 3、判断客户端为移动端或pc端

{% highlight javascript %}
var isMobile =  navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i)
if (isMobile) {
    console.log('mobile')
} else {
    console.log('pc')
}
{% endhighlight %}

#### 4、善用伪元素

使用伪元素