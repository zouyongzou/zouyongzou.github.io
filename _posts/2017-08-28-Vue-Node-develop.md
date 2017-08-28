---
layout:   post
title:    "Vue + Node 开发"
date:     2017-4-28
excerpt:  搭建了一个 Vue + Node + MySQL 的项目。前端用 Vue 开发页面，路由通过 axios 实现；后端用 Node 开发 api
tags:     [Vue, Node]
comments: true
---

#### 开发流程
1. 前后端分离。前端用 Vue 开发页面，路由通过 axios 实现；后端用 Node 开发 api
2. 前端开发修改 Vue-cli 提供的 proxyTable 进行代理，跨域调用

#### 具体实现
1.在 Vue 项目的根目录下新建 server 目录，存放服务器相关文件，进入 server 目录，新建三个 js 文件，安装 express。    
-index.js（入口文件）   
-db.js（数据库操作）    
-api.js（api 开发）   

{% highlight javascript %}
// server/index.js
// 引入编写好的api
const api = require('./api')
// 引入文件模块
const fs = require('fs')
// 引入处理路径的模块
const path = require('path')
// 引入处理post数据的模块
const bodyParser = require('body-parser')
// 引入Express
const express = require('express')
const app = express()

app.use(bodyParser.json())
app.use(bodyParser.urlencoded({extended: false}))
app.use(api)
// 访问静态资源文件 这里是访问所有dist目录下的静态资源文件
app.use(express.static(path.resolve(__dirname, '../dist')))
// 因为是单页应用 所有请求都走/dist/index.html
app.get('*', function (req, res) {
  const html = fs.readFileSync(path.resolve(__dirname, '../dist/index.html'), 'utf-8')
  res.send(html)
})

var port = 8081
var uri = 'http://localhost:' + port

// 监听端口
app.listen(port)
console.log('\n> Starting server...')
console.log('> Listening at ' + uri + '\n')
{% endhighlight %}

{% highlight javascript %}
// server/db.js
// MySQL数据库连接配置
module.exports = {
  mysql: {
    host: '127.0.0.1',
    user: 'root',
    password: 'zouyong',
    database: 'my_db',
    port: 3306
  }
}
{% endhighlight %}

{% highlight javascript %}
// server/api.js
var mysql = require('mysql')
var express = require('express')
var router = express.Router()

var db = require('./db')
// var $sql = require('./userSqlMapping');

// util
var extend = function (target, source, flag) {
  for (var key in source) {
    if (source.hasOwnProperty(key)) {
      flag ? (target[key] = source[key]) : (target[key] === void 0 && (target[key] = source[key]))
    }
  }
  return target
}

// 使用连接池，提升性能
var pool = mysql.createPool(extend({}, db.mysql))

// 向前台返回JSON方法的简单封装
var jsonWrite = function (res, ret) {
  if (typeof ret === 'undefined') {
    res.json({
      code: '1',
      msg: '操作失败'
    })
  } else {
    res.json(ret)
  }
}

// 查询所有用户
router.get('/api/queryAll', function (req, res, next) {
  pool.getConnection(function (err, connection) {
    if (err) return err
    connection.query('SELECT * FROM user', function (err, result) {
      if (err) return err
      jsonWrite(res, result)
      connection.release()
    })
  })
})

module.exports = router

{% endhighlight %}

2.开启代理服务。因为 Vue 项目开发时，会自动开启一个8080端口的服务器，而后端为8081，造成了跨域。进入project-name/config/index.js 可设置开启代理服务。

{% highlight javascript %}
...
 proxyTable: {
        '/api': {
        target: 'http://localhost:8081/api/',
        changeOrigin: true,
        pathRewrite: {
          '^/api': ''
        }
      }
    }
...
{% endhighlight %}
具体配置可参考[官方文档](https://vuejs-templates.github.io/webpack/proxy.html)

###### [原文](http://blog.csdn.net/qq_26598303/article/details/53468399)