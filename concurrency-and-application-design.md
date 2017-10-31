# Concurrency and Application Design {#pageTitle}

高效的使用多个线程存在困难，没办法获取可用内核数，线程同步问题。苹果系统提供了更好的异步方法

## The Move Away from Threads

线程不能根据系统负载情况动态调整

GCD把线程管理的任务交给了系统内核

Operation Queue负责线程管理、执行异步任务

## Asynchronous Design Techniques

## Performance Implications

## Concurrency and Other Technologies



