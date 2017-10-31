# Dispatch Queues

## About Dispatch Queues

dispatch queues类型

* Serial \(private dispatch queues\)
* Concurrent \(global dispatch queue\)：系统提供四种预定义的Queue
* Main dispatch queue

相比于锁，线性dispatch Queue主要在应用进程空间工作，只有在发生竞争的时候才调用内核

dispatch queues的其他特点

* Dispatch queues执行并行任务时会考虑到其他的Dispatch queues，串行任务仅限于一个Dispatch queue内
* 系统决定执行多少个任务
* 系统执行新任务时会考虑Queue的优先级
* 不同于Operation object，放进dispatch Queue中的任务必须处于就绪状态
* Private dispatch queues是引用计数对象

## Queue-Related Technologies

| Technology | Description |
| :--- | :--- |
| Dispatch groups | 监听一组block对象执行完毕 |
| Dispatch semaphores | 只有信号量不可用时，才调用内核 |
| Dispatch sources |  |

## Implementing Tasks Using Blocks

## Creating and Managing Dispatch Queues

## Adding Tasks to a Queue

## Suspending and Resuming Queues

## Using Dispatch Semaphores to Regulate the Use of Finite Resources

## Waiting on Groups of Queued Tasks

## Dispatch Queues and Thread Safety

## 



