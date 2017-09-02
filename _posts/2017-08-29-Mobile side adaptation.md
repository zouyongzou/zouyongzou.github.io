---
layout:   post
title:    "移动端适配方案"
date:     2016-11-7
excerpt:  分析介绍移动端适配的解决方案。
tags:     [Web]
#comments: true
---
### 像素
##### 设备像素
屏幕的物理像素，任何设备屏幕的物理像素的数量都是固定不变的，单位是 pt。

##### CSS 像素
CSS 像素也可以称为设备独立像素(device-independent pixels)，简称为 dips，单位是 dp。

##### 视口（viewport）
浏览器显示页面内容的屏幕区域
viewport元标签和属性
{% highlight javascript %}
<meta name="viewport" content="width=device-width; initial-scale=1.0; maximum-scale=1.0; user-scalable=no;">
{% endhighlight %}

Values for the content of \<meta name="viewport"\>

| value | 取值 | 含义 |
|:--------|:-------:|--------:|
| width | 正整数或 device-width | 定义 viewport 的宽度 |
| height | 正整数或 device-height | 定义 viewport 的宽度（Not used by any browser.） |
| initial-scale | 0.0 ~ 10.0 | 定义初始缩放值 |
| maximum-scale | 0.0 ~ 10.0 | 定义最大缩小比例，>= minimum-scale |
| minimum-scale | 0.0 ~ 10.0 | 定义最小缩小比例，<= maximum-scale |
| user-scalable | yes or no  | 是否允许缩放，默认为yes |
{: rules="groups"}

