# Concurrency and Application Design {#pageTitle}

高效的使用多个线程存在困难，没办法获取可用内核数，线程同步问题。苹果系统提供了更好的异步方法

## The Move Away from Threads

线程不能根据系统负载情况动态调整

GCD把线程管理的任务交给了系统内核

Operation Queue负责线程管理、执行异步任务

#### Dispatch Queues

基于C语言，先进先出的串行或者并行执行任务

Dispatch queues其他优势

* 接口简单
* 提供自动的整体的线程池管理
* 通过优化提升速度
* 更高效的使用内存，因为线程栈不在应用内存空间
* 不中断内核
* 向队列中异步分发任务不会导致队列死锁
* 根据系统负载情况动态调整
* 线性队列高效的替代了锁和其他同步机制

#### Dispatch Sources

基于C语言异步处理特定类型的系统事件

事件发生时，dispatch source将block添加到dispatch queue中

dispatch source能监测的系统事件

* Timers
* Signal handlers
* Descriptor-related events
* Process-related events
* Mach port events
* Custom events that you trigger

#### Operation Queues

除了支持先进先出，还支持依赖

Operation objects会发出KVO通知

## Asynchronous Design Techniques

合理选择是否使用并行，不合理的使用并行反而会降低程序的效率

#### Define Your Application’s Expected Behavior

#### Factor Out Executable Units of Work

#### Identify the Queues You Need

dispatch queue：并行和串行

operation objects：添加依赖

#### Tips for Improving Efficiency

* 考虑到内存使用时，在任务中直接计算结果，不去内存加载

* 尽量把串行的任务并行

* 避免使用锁

* 尽量使用系统框架

## Performance Implications

[_Performance Overview_](https://developer.apple.com/library/content/documentation/Performance/Conceptual/PerformanceOverview/Introduction/Introduction.html#//apple_ref/doc/uid/TP40001410)

## Concurrency and Other Technologies

#### OpenCL and Concurrency

在GPU里面进行大量数据运算，传入传出数据的成本较高，不是所有场合都适合使用的

[_OpenCL Programming Guide for Mac_](https://developer.apple.com/library/content/documentation/Performance/Conceptual/OpenCL_MacProgGuide/Introduction/Introduction.html#//apple_ref/doc/uid/TP40008312)

#### When to Use Threads

对实时性要求较高时使用

[_Threading Programming Guide_](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/Multithreading/Introduction/Introduction.html#//apple_ref/doc/uid/10000057i)

