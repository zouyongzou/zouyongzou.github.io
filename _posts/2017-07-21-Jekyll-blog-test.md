---
title:    "Jekyll 搭建博客（测试）"
date:     2016-04-15
excerpt:  Jekyll 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过 Markdown （或者 Textile） 以及 Liquid 转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。
tags:     [Jekyll]
---

本文为测试文章，具体搭建详情请移步[ Jekyll 官网](http://jekyll.com.cn/docs/home/)
{: .notice--warning}

## 1、Jekyll 介绍
Jekyll 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过 Markdown （或者 Textile） 以及 Liquid 转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。Jekyll 也可以运行在 GitHub Page 上，也就是说，你可以使用 GitHub 的服务来搭建你的项目页面、博客或者网站，而且是完全免费的。

## 2、安装
Jekyll 基于 Ruby 运行，首先得安装[ Ruby ](https://www.ruby-lang.org/en/downloads/)和[ RubyGems](https://rubygems.org/pages/download)，可自行选择下载相应版本。windows 下可以使用 Jekyll running on Windows，官方文档并不建议在 Windows 平台安装 Jekyll。gems 是 Ruby 的一个打包工具和包安装工具。安装成功后，打开终端：
```
$ gem install jekyll
```
如安装中碰到问题，可去 [troubleshooting](http://jekyll.com.cn/docs/troubleshooting/) 或者 [report an issue](https://github.com/jekyll/jekyll/issues/new) 

```
// 生成 Jekyll 模板
~ $ gem install jekyll
~ $ jekyll new myblog
~ $ cd myblog
~/myblog $ jekyll serve
// => Now browse to http://localhost:4000
```
ps：如果 jekyll serve 失败，可查看错误信息，看是否有相关依赖包未安装。
## 3、基本用法
```
$ jekyll build
// => 当前文件夹中的内容将会生成到 ./site 文件夹中。

$ jekyll build --destination <destination>
// => 当前文件夹中的内容将会生成到目标文件夹<destination>中。

$ jekyll build --source <source> --destination <destination>
// => 指定源文件夹<source>中的内容将会生成到目标文件夹<destination>中。

$ jekyll build --watch
// => 当前文件夹中的内容将会生成到 ./site 文件夹中，
//    查看改变，并且自动再生成。

jekyll serve
// => 一个开发服务器将会运行在 http://localhost:4000/

$ jekyll serve --detach
// => 功能和`jekyll serve`命令相同，但是会脱离终端在后台运行。
//    如果你想关闭服务器，可以使用`kill -9 1234`命令，"1234" 是进程号（PID）。
//    如果你找不到进程号，那么就用`ps aux | grep jekyll`命令来查看，然后关闭服务器。[更多](http://unixhelp.ed.ac.uk/shell/jobz5.html).

$ jekyll serve --watch
// => 和`jekyll serve`相同，但是会查看变更并且自动再生成。
```
## 4、目录结构
```
// 基本的 Jekyll 网站的目录结构
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _data
|   └── members.yml
├── _site
└── index.html
```
用途：

| 文件/目录 | 描述 |
|:--------|:-------:|--------:|
| _config.yml | 保存配置数据 |
| _drafts | 未发布文章 |
| _includes | 加载到布局或者文章中以方便重用 |
| _layouts | 包裹在文章外部的模板 |
| _posts | 文章。YEAR-MONTH-DAY-title.MARKUP |
| _data | 格式化站点数据 |
| _site | Jekyll 完成转换，存放页面（.gitignore ） |
| index.html  |包含 YAML 头信息部分，Jekyll 自动转换 |
| Other Files/Folders | 完全拷贝到生成的 site 中 
{: rules="groups"}
