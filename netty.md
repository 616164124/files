# Netty

[TOC]



## BIO

​	每链接，占用一个线程，cpu单位时间内，每一个线程轮一下除了要跑进程的逻辑，还要有一些列其他的内核操作，比较浪费cpu资源， 因为进程（线程太多）。

​	



