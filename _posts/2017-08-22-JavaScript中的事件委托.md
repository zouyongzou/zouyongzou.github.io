---
layout:   post
title:    "JavaScript 中的事件委托"
date:     2016-04-22
excerpt:  事件委托：利用事件冒泡，只指定一个事件处理程序，就可以管理某一类型的所有事件。即把事件加到父级上，触发执行效果。
tags:     [JavaScript]
conments: true;
---

##### 事件委托：利用事件冒泡，只指定一个事件处理程序，就可以管理某一类型的所有事件。即把事件加到父级上，触发执行效果。
优点:
###### 1、提高性能
###### 2、动态添加节点之后还会有之前的事件。
例子：为每一个li添加事件
{% highlight html %}
<ul>
    <li></li>
    <li></li>
    <li></li>
</ul>
{% endhighlight html %}

{% highlight javascript %}
// 不使用事件委托
for (var i = 0; i < li.length; i++) {
  li[i].onmouseover = function() {
    this.style.background = "#7cf";
  },
  li[i].onmouseout = function() {
    this.style.background = "";
  }
}
{% endhighlight javascript %}

这样就为所有<li>添加了鼠标事件，但有多个<li>时比较影响性能。

下面使用事件委托的方式：

**基本概念**  
事件源：event对象，操作的元素就是事件源。  
ie：window.event.srcElement  
标准下：event.target  
nodeName：找到元素的标签名
{: .notice}

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
{% endhighlight javascript %}
