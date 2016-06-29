---
layout: post
title: GCD之dispatch_barriers_async
description: "GCD之dispatch_barriers_async"
tags: [GCD post]
image:
  background: triangular.png
---

当你访问数据库或文件时为了提升效率会采用并发的dispatch queues去读取数据或文件。而此时可能有其他的线程队列任务在修改同一文件，在这种情况下你读取的可能会是脏数据。这就是读者-写者问题。

GCD提供的dispatch_barriers_async函数可解决此问题。下列代码表示有7个读取任务，一个写任务：

~~~ ruby
 dispatch_async(queue, blk0_for_reading);
 dispatch_async(queue, blk1_for_reading); 
 dispatch_async(queue, blk2_for_reading); 
 dispatch_async(queue, blk3_for_reading); 
 dispatch_barrier_async(queue, blk_for_writing); 
 dispatch_async(queue, blk4_for_reading); 
 dispatch_async(queue, blk5_for_reading); 
 dispatch_async(queue, blk6_for_reading); 
 dispatch_async(queue, blk7_for_reading);
~~~


