# 简介

这是一套经过长时间实盘验证，有超过100亿美金交易量，包含数据录入，风控，但不包含具体交易逻辑的架构实现

你可以利用它简单，低成本的实现你的交易逻辑，其大量运用阿里云分布式服务器进行架构，以及飞书进行异常报错，交易信息...

# 最大优势

低成本，高效率，简单实现是这套系统的三个优势

不到1000人民币一个月的成本，实现每分钟扫描200个交易对，接近7万次循环

除了撮合服务器（C++）外都采用python编写，简单易懂

大量的分布式架构实现更快的速度，并且可以根据个人需求，自由伸缩的调控服务器数量来实现成本和性能的平衡

# 架构解析

该系统通过一个C++服务器作为撮合服务器，大量的分布式python服务器作为数据采集服务器，将采集的数据，包括Kline ，trades，tick等，喂给C++服务器，交易服务器再从C++服务器统一读取数据的方式，并且在本地端维护一个K线账本的方式，来避开交易所的频率限制，实现高效率

又比如，账户的余额，持仓数据，在币安上有三种方式获取，a是position risk，b是account，c是ws，那么会有三台服务器分别采用这三种方式读取，然后汇入C++服务器进行校对，通过对比更新时间截取最新的数据，然后服务给交易服务器

# 作者自述

2021年，我从一家顶级的量化公司辞职后，跟朋友一起做起量化交易，主要战场在币安，这两年间，我们从做市商->趋势->套利等类型均有涉及，最高峰的时候，在币安一个月有接近10亿美金的交易额。

至2023年7月，因为各种原因，大方向上失败了，只遗留下极少资金还在继续运行一个比较稳定盈利的左侧交易策略。

这是在这两年时间里面探索出来的一套高效率，低成本的数据读取，录入框架，同时包含了一套风控系统，他更像一个架构，而不是一个实现，你同样可以简单的运用到okex，bybit等等上

目前本人在艰难的寻求资金合作或者工作机会中，如能提供帮助请联系 c.binance.quant@gmail.com


