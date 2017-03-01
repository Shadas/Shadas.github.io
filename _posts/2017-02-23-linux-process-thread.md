---
layout: post
#标题配置
title:  golang goroutine 调度
#时间配置
date:   2017-03-01 14:23:00 +0800
#大类配置
categories: golang
#小类配置
tag: 
---


* content
{:toc}


golang 的高并发特性其中之一就是来源于特有的 goroutine 协程的实现。

golang 是原生支持语言级并发的，这个并发的最小逻辑单元就是goroutine。goroutine可以看做是 Go 语言提供的一种用户态线程，这种用户态线程是跑在内核级线程之上的。当我们创建了若干个goroutine，并且它们都跑在同一个内核级线程的时候，就需要一个调度器来维护这些goroutine，使之都可以使用cpu资源，并且尽量做到公平。

本篇笔记主要记录一下调度器的使用原理。

