---
layout:   post
title:    "基本语法-Github Pages 主题（Moon）"
date:     2016-04-15
tags:     [markdown, jekyll]
feature:  /assets/img/images/github-icon-a.png
comments: true
---

### 前言
主题语法基于markdown，在两行三虚线包含的为 YAML 的格式的头部信息。
<!--more-->

### 表格

| Header1 | Header2 | Header3 |
|:--------|:-------:|--------:|
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|----
| cell1   | cell2   | cell3   |
| cell4   | cell5   | cell6   |
|=====
| Foot1   | Foot2   | Foot3
{: rules="groups"}

### 代码块

{% highlight css %}
#container {
  float: left;
  margin: 0 -240px 0 0;
  width: 100%;
}
{% endhighlight %}

### 按钮

{% highlight html %}
<a href="#" class="btn btn-success">Success Button</a>
{% endhighlight %}

<div markdown="0"><a href="#" class="btn">Primary Button</a></div>
<div markdown="0"><a href="#" class="btn btn-success">Success Button</a></div>
<div markdown="0"><a href="#" class="btn btn-warning">Warning Button</a></div>
<div markdown="0"><a href="#" class="btn btn-danger">Danger Button</a></div>
<div markdown="0"><a href="#" class="btn btn-info">Info Button</a></div>

### KBD

`<kbd>` 标签

{% highlight html %}
<kbd>W</kbd><kbd>A</kbd><kbd>S</kbd><kbd>D</kbd>
{% endhighlight %}

按 <kbd>W</kbd><kbd>A</kbd><kbd>S</kbd><kbd>D</kbd> 移动

### Notices

**Watch out!** 在段落中插入`{: .notice}` 来添加notices.
{: .notice}

### 数学公式

~~~
行内渲染：\\( 1/x^{2} \\)
块级渲染：\\[ \frac{1}{n^{2}} \\]
~~~

行内渲染：\\( 1/x^{2} \\)        
块级渲染：\\[ \frac{1}{n^{2}} \\]

公式内嵌于 `\\[ ... \\]` 和 `\\( ... \\)` 

### 代码块语法高亮

通过修改 `/assets/css/syntax.css` 文件

### 引用注释

欢迎关注我的GitHub[^1]，谢谢

[^1]: 我的GitHub地址为：<https://github.com/zouyongzou>

### 插入图片

#### 一张图片
```
<figure>
    <a href="{{ site.url }}/assets/img/images/github-icon-a.png">
        <img src="{{ site.url }}/assets/img/images/github-icon-a.png">
        <figcaption>我是GitHub，看我可爱吗</figcaption>
    </a>
</figure>
其中 a标签href为放大后的图片，img为缩略图
```
<figure>
    <a href="{{ site.url }}/assets/img/images/github-icon-a.png"><img src="{{ site.url }}/assets/img/images/github-icon-a.png"></a>
</figure>

#### 多张图片
两张为“half”，三张为“third”
<figure class="half">
    <a href="{{ site.url }}/assets/img/images/github-icon-a.png"><img src="{{ site.url }}/assets/img/images/github-icon-a.png"></a>
    <a href="{{ site.url }}/assets/img/images/github-icon-a.png"><img src="{{ site.url }}/assets/img/images/github-icon-a.png"></a>
</figure>

#### 其他方法
{% highlight liquid %}
{% raw %}
{% capture images %}
    {{ site.url }}/assets/img/images/github-icon-a.png
    {{ site.url }}/assets/img/images/github-icon-a.png
    {{ site.url }}/assets/img/images/github-icon-a.png
{% endcapture %}
{% include gallery images=images caption="Test images" cols=3 %}
{% endraw %}
{% endhighlight %}

参数：

- `caption`: 作用同<figcaption>标签;
- `cols`: 设置列个数。
可用值: [1,2,3].

效果如图：
{% capture images %}
    {{ site.url }}/assets/img/images/github-icon-a.png
    {{ site.url }}/assets/img/images/github-icon-a.png
    {{ site.url }}/assets/img/images/github-icon-a.png
{% endcapture %}
{% include gallery images=images caption="多张图片" cols=3 %}

### 插入背景图片

在头信息中加入
~~~
feature: http://i.imgur.com/Ds6S7lJ.png
~~~
url为http或https

### 插入视频
{% highlight html %}
<iframe width="560" height="315" src="//www.youtube.com/embed/SU3kYxJmWuQ" frameborder="0"> </iframe>
{% endhighlight %}