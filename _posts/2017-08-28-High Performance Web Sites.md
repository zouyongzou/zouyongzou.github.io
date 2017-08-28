---
layout:   post
title:    "高性能网站建设指南"
date:     2017-7-7
excerpt:  《高性能网站建设指南》一书给出快速加载网站的14条规则，便于开发人员优化网站性能。
tags:     [Web]
---

###### [代码案例](http://stevesouders.com/hpws/rules.php)
#### 规则 1————减少HTTP请求
***图片地图（Image Maps）：***使用 map 标签进行映射  
***CSS Sprites：***合并图片减少HTTP请求，利用了 background-position 属性  
***内联图片（Inline Images）：***data URI scheme。具体内容可见 MDN 中 [Data URLs](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/data_URIs)  
***合并脚本和样式表***

#### 规则 2————使用内容发布网络
***内容发布网络（Content Delivery NetWorks）：***CDN 是一组分布在多个不同地理位置的 Web 服务器。

#### 规则 3————添加 Expires 头
***Expires 头：***设置缓存（服务器和客户端时间严格同步；过期后处理）  
***Max-Age 和 mod_expires：***Cache-Control 使用 max-age 指令指定组件被缓存多久（单位：秒），可消除 Expires 的限制

#### 规则 4————压缩组件
***压缩组件：***设置 HTTP 请求中的 Accept-Encoding：gzip, deflate

#### 规则 5————将样式表放在顶部

#### 规则 6————将脚本放在底部

#### 规则 7————避免 CSS 表达式

#### 规则 8————使用外部 JavaScript 和 CSS

#### 规则 9————减少 DNS 查找 

#### 规则 10————精简 JavaScript（混淆）

#### 规则 11————避免重定向

#### 规则 12————移除重复脚本

#### 规则 13————配置 ETag
***ETag：***实体标签（Entity Tag）是 Web 服务器和浏览器用于确认缓存组件的有效性的一种机制。

#### 规则 14————使 Ajax 可缓存
