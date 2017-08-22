---
layout:   post
title:    "艺师汇项目总结（mobile 端）"
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
navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i)
{% endhighlight %}


{% highlight javascript %}
// 使用事件委托
ul.onmouseover = function(e) {
  var e = e||window.event;
  var target = e.target||e.srcElement;

  if (target.nodeName.toLowerCase() == "li") {
    target.style.background = "#7cf";
  }
}

ul.onmouseout = function(e) {
  var e = e||window.event;
  var target = e.target||e.srcElement;

  if (target.nodeName.toLowerCase() == "li") {
    target.style.background = "";
  }
}
{% endhighlight %}

##### 4、姐姐