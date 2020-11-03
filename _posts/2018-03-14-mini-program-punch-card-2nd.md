---
title: "小程序从开发到上线（二）- 搭建生产环境"
excerpt: "在 nginx 服务器上安装 Python3、mongoDB 和 supervisor，以及如何使用 supervisor 管理进程"
comments: true
search: true
tag: [小程序]
toc: true
toc_sticky: true
---
## 1、安装 nginx
在 CentOS 上，可直接使用 yum 来安装 nginx
```bash
yum install nginx -y
```
安装完成后，使用 nginx 命令启动 nginx：

```bash
nginx
```
此时，访问 http://\<服务器 ip\> 可以看到 nginx 的测试页面

> 如果无法访问，用 nginx -s reload 命令重启 nginx

## 2、安装 Python3
### 2.1 准备工作
查看当前系统中的 Python 版本（当前为 Python 2.7）
```bash
python --version
```
查看 CentOS 版本
```bash
cat /etc/redhat-release
```
安装开发工具包，避免后续安装出错  
```bash
# 安装 Development Tools
yum groupinstall -y "Development tools"

# 安装其它工具包
yum install -y zlib-devel bzip2-devel openssl-devel ncurses-devel sqlite-devel
```
### 2.2 下载、编译和安装 Python3  
推荐从 [官网](https://www.python.org/downloads/source/) 下载相应的版本（右键复制链接地址），最好与本地开发环境保持一致，避免一些不必要的问题。  
这里下载的是最新版 Python 3.7.0
```bash
# /usr/local/python3
wget https://www.python.org/ftp/python/3.7.0/Python-3.7.0.tgz
```
下载完成后，解压安装包
```bash
tar zxvf Python-3.7.0.tgz
```
进入 Python-3.7.0 文件夹
```bash
cd Python-3.7.0
```
执行 configure 文件预编译
```bash
./configure
```
编译和安装
```bash
make && make install
```

### 2.3 配置 Python3  
更新系统默认 Python 版本  
先把系统默认的旧版 Python 重命名
```bash
mv /usr/bin/python /usr/bin/python.old
```
再删除系统默认的 python-config 软链接
```bash
rm -f /usr/bin/python-config
```
最后创建新版本的 Python 软链接，类似 windows 下的快捷方式
```bash
ln -s /usr/local/bin/python3 /usr/bin/python
```
```bash
ln -s /usr/local/bin/python3-config /usr/bin/python-config
```
```bash
ln -s /usr/local/include/python3.7/ /usr/include/python3.7
```

usr 指 Unix System Resource  
`/usr/bin`目录是系统预装的可执行程序，会随系统升级而改变  
`/usr/local/bin`目录是给用户安装的可执行程序，不会随系统升级而改变 
{: .notice--primary}

编辑`/usr/bin/yum`文件
```bash
vim /usr/bin/yum
```
把代码第一行的 python 改为指向老的 python2.7 版本，修改内容参考以下：
```python
#!/usr/bin/python2.7
```
CentOS6 只要修改 `/usr/bin/yum`   
CentOS7 需要同时修改 `/usr/bin/yum` 以及 `/usr/libexec/urlgrabber-ext-down`
{: .notice--warning}
检查 Python 版本是否为 Python3.x
```bash
python --version
```
查看 pip3 版本
```bash
pip3 --version
```
安装 pip3
```bash
curl https://bootstrap.pypa.io/get-pip.py | python
```
> 因为版本不同，可能会出现错误，请仔细分析错误信息，检查路径、链接是否正确。如果找不到原因，请 google。

## 3、安装 MongoDB

使用 yum 上安装 MongoDB：
```
yum install mongodb-server mongodb -y
```
安装成功后，查看安装的版本：
```
mongod --version
mongo --version
```
启动 MongoDB
创建目录，用于 MongoDB 数据和日志存储：
```
mkdir -p /data/mongodb
mkdir -p /data/logs/mongodb
```
创建后，使用下面的命令来启动 MongoDB：
```
mongod --fork --dbpath /data/mongodb --logpath /data/logs/mongodb/weapp.log
```
检查是否启动成功 
```
netstat -ntpl | grep 27017
```
> MongoDB 默认端口为 27017，查看 27017 端口是否被 MongoDB 的进程占用，来检查是否启动成功

添加 MongoDB 用户
登录本地 MongoDB 服务：
```
mongo
```
登录后，创建一个用户 zou:
```
use zou;
db.createUser({ user: 'zou', pwd: '123456', roles: ['dbAdmin', 'readWrite']});
```
创建完成后，使用 exit 或 ctrl+c 退出命令行工具。
> 创建的用户和密码将用于下一步中连接数据库时使用，如果使用不同的用户或密码，注意要保存好

## 4、Supervisor 安装与配置
Supervisor 是基于 Python 的进程管理工具，只能运行在 Unix-Like

## 5、Hello, world!
到这一步，所有环境都已搭建完成，现在来写点代码测试一下：