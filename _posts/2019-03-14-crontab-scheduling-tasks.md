---
title: "crontab 设置定时任务"
excerpt: "crontab 命令常见于 Unix 和类 Unix 的操作系统之中，用于设置周期性被执行的指令或 shell script脚本。"
comments: true
search: true
tags: [Linux]
---

crontab 命令常见于 Unix 和类 Unix 的操作系统之中，用于设置周期性被执行的指令或 shell script脚本。
周期性的单位可以是分钟、小时、日、月、周及以上的任意组合。适合周期性的日志分析或数据备份等工作。

下面在 macOS 使用 man crontab 查看信息，不同操作系统会有差别
{: .notice}

<img src="{{ site.url }}{{ site.baseurl }}/assets/images/blog/2019031401.png" alt="" class="full">

### 命令格式
```
crontab [-u user] file
crontab [-u user] { -l | -r | -e }
```
- -u user: 只有 root 才能进行这个任务，创建/删除某个用户的 crontab 服务;  
（file: file 是命令文件名，表示将 file 作为 crontab 的任务列表文件载入 crontab。如果没有指定这个 file，crontab 命令将接受标准输入（键盘）上键入的命令，并载入）
- -l: 显示 crontab 文件内容
- -r: 删除 crontab 文件内容，**若要删除一项，用 -e 去编辑**。
- -e: 编辑 crontab 文件内容。

### crontab 语法
语法示例如下:
```bash
# .---------------- 分 (0 - 59)
# |  .------------- 时 (0 - 23)
# |  |  .---------- 日 (1 - 31)
# |  |  |  .------- 月 (1 - 12)
# |  |  |  |  .---- 周 (0 - 7)
# |  |  |  |  |
  *  *  *  *  *  command to be executed
```
值得注意的是: 0 或 7 都代表周日。  
并且还有一些特殊的字符：  
**\*** : 允许所有值  
**,** : 允许指定多个值，前后不能有空格  
**-** : 允许定义范围  
**/** : 允许指定单位重复  

#### 实例
```
# 每1分钟执行一次
* * * * * command

# 每天的9点和18点执行一次
0 9,18 * * * command

# 每天的12点到14点执行一次
0 12-14 * * * command

# 每隔两天的18点执行一次
0 18 */2 * * command

# 每周五的18点执行一次
0 18 * * 5 command
```

### 注意事项

#### 环境变量问题
脚本中涉及文件路径时写全局路径；

#### 清理邮件日志
