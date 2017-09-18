---
layout:   post
title:    "CSS 常用的几种水平垂直居中的方法"
date:     2016-12-1
excerpt:  使用 CSS 实现元素水平垂直居中，在工作或者面试中总会经常遇到，本文总结了一些常用的水平垂直居中的方法。
tags:     [CSS]
comments: true
---

使用 CSS 实现元素水平垂直居中，在工作或者面试中总会经常遇到，所以本文总结了一些常用的水平垂直居中的方法。

#### 一、文本的水平垂直居中（单行文本）
文本的水平垂直居中实现比较简单，只需要设置 line-height 与 height 相等，text-align: certer
{% highlight html %}
<div class="text">
    水平垂直居中
</div>
{% endhighlight %}
{% highlight css %}
.text {
    height: 36px;
    line-height: 36px;
    text-align: center;
}
{% endhighlight %}

#### 二、块元素的水平垂直居中
以下示例 HTML 结构均为
{% highlight html %}
  <div class="parent">
    <div class="child"></div>
  </div>
{% endhighlight %}

##### 1、position + margin: auto（常用）
{% highlight css %}
.parent {
    position: relative;
    width: 300px;
    height: 300px;
    background: #0f0f0f;
}
.child {
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    right: 0;
    margin: auto;
    /* 宽高仅为示意 */
    width: 100px;
    height: 100px;
    background: #f0f0f0;
}
{% endhighlight %}
优点：自适应、简单粗暴  
缺点： 未发现  
原理：当一个绝对定位元素，其对立定位方向属性同时有具体定位数值的时候，会发生流体特性。如果只有 left 或 right 属性，则由于包裹性，此时 .child 宽度是 0。但是，在本例中，因为 left/right 同时存在，因此宽度就不是 0，而是自适应于 .child 包含块的 padding box 宽度，也就是随着包含块 padding box 的宽度变化，.box 的宽度也会跟着一起变。  
具有流体特性绝对定位元素的 margin: auto 的填充规则和普通流体元素一模一样：  
① 如果一侧定值，一侧 auto，auto 为剩余空间大小；  
② 如果两侧均是 auto, 则平分剩余空间；
##### 2、position + 负 margin
{% highlight css %}
.parent {
    position: relative;
    width: 300px;
    height: 300px;
    background: #0f0f0f;
}
.child {
    position: absolute;
    left: 50%;
    top: 50%;
    margin: -50px 0 0 -50px;  /* 宽高的一半 */
    width: 100px;
    height: 100px;
    background: #f0f0f0;
}
{% endhighlight %}
优点：兼容性好  
缺点：需要知道子元素的宽高，否则无法设置负 margin
##### 3、position + transform
{% highlight css %}
.parent {
    position: relative;
    width: 300px;
    height: 300px;
    background: #0f0f0f;
}
.child {
    position: absolute;
    left: 50%;
    top: 50%;
    /* 宽高仅为示意 */
    width: 100px;
    height: 100px;
    transform: translate(-50%, -50%);  /* 50%为自身尺寸的一半 */
    background: #f0f0f0;
}
{% endhighlight %}
优点：不需要知道子元素的宽高  
缺点：兼容性不好

本文简单介绍了洒家在开发中经常使用的几种水平垂直居中的几种方法，当然还有很多其它的需求及解决方法，可自行搜索学习。

（完）