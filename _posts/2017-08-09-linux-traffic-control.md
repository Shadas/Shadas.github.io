---
layout: post
#标题配置
title:  linux 流量控制
#时间配置
date:   2017-08-09 19:23:00 +0800
#大类配置
categories: linux
#小类配置
tag: 
---

* content
{:toc}

有时我们需要模拟不良网络情况下系统程序的表现和性能，为此可能会用到以下工具。

### 流量控制工具 tc

```
tc qdisc add dev eth0 root netem delay 100ms	//延时
tc qdisc del dev eth0 root netem delay 100ms

tc qdisc add dev eth0 root netem loss 20% 25%	//丢包
tc qdisc del dev eth0 root netem loss 20% 25%

tc qdisc list
```

tc控制的是服务器outbound的流量，如果需要控制inbound的，可能需要其他的工具。