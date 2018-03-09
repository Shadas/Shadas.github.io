---
layout: post
#标题配置
title:  supervisor的配置及使用
#时间配置
date:   2018-03-09 10:17:26 +0800
#大类配置
categories: linux
#小类配置
tag: 工具
---


* content
{:toc}

## 概述

supervisor 是一个守护进程的工具，主要用于任务的运行情况维护，保证进程可用。

## 安装

### ubuntu 系统

```
apt-get install supervisor
```

## 配置文件

supervisor的主配置文件为：

```
/etc/supervisor/supervisord.conf
```

子任务的配置文件推荐放在目录：

```
/etc/supervisor/conf.d/
```

加载配置文件：

```
supervisorctl reload
```

## 任务控制

### 交互式命令

```
$ supervisorctl  //进入命令行交互模式
example                          STOPPED   Mar 09 10:41 AM
supervisor> start example // 启动任务 example
example: started
supervisor> status //查看任务列表状态
example                          RUNNING   pid 6701, uptime 0:01:05
supervisor> restart example // 重启任务 example
example: stopped
example: started
supervisor> stop all // 停止所有任务
example: stopped
supervisor> start all // 启动所有任务
example: started
supervisor> restart all // 重启所有任务
example: stopped
example: started
supervisor> exit // 退出交互界面
$
```

### 非交互式命令

```
$ supervisorctl restart example // 重启 example 项目
example: stopped
example: started
$ supervisorctl restart all // 重启所有项目
example: stopped
example: started
... //具体命令以此类推
```