# Operation Queues

可单独使用也可以和Operation Queue配合使用

## About Operation Objects

| Class | Description |
| :--- | :--- |
| NSInvocationOperation | 适用于已有代码 |
| NSBlockOperation | 所有关联的block都执行完，Operation才算执行完。[_Blocks Programming Topics_](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/Blocks/Articles/00_Introduction.html#//apple_ref/doc/uid/TP40007502) |
| NSOperation | 完全控制 |

所有Operation Object都支持的特性

* 基于图的依赖
* 支持completion block
* 监听Operation的执行状态
* 改变线程优先级
* 支持取消

## Concurrent Versus Non-concurrent Operations

Operation加入到Queue中，默认是并行的

单独使用Operation，默认是串行的，如果想要并行，需要确保start在其他线程被调用

## Creating an NSInvocationOperation Object

## Creating an NSBlockOperation Object

该Operation包含了一个或多个block，执行时，它将这些block放进默认优先级的concurrent dispatch queue，当所有的block都执行完时，将自己置为结束

## Defining a Custom Operation Object

#### Performing the Main Task

* \(required\)A custom initialization method
* \(required\)main
* \(optional\)main方法里面调用的其他方法
* \(optional\)访问器方法
* \(optional\)NSCoding

#### Responding to Cancellation Events

被cancel的线程还需要自己进行检测

应该调用isCancelled的情况：实际任务之前、每次循环、容易退出的位置

#### Configuring Operations for Concurrent Execution

并行Operation需要覆盖的方法

```
start(Required) 
main(Optional) 
isExecuting(Required) 
isFinished(Required) 
isConcurrent(Required)
```

被cancel的线程也需要更新finish状态

#### Maintaining KVO Compliance

```
isCancelled
isConcurrent
isExecuting
isFinished
isReady
dependencies
queuePriority
completionBlock
```

## Customizing the Execution Behavior of an Operation Object

#### Configuring Interoperation Dependencies

可以在不同的Queue中的Operation之间建立以来，但是要避免循环依赖

#### Changing an Operation’s Execution Priority

优先级只限于同一个Queue中的线程

高优先级的线程不一定比低优先级的线程先执行，还要看是否处于ready状态

#### Changing the Underlying Thread Priority

#### Setting Up a Completion Block

## Tips for Implementing Operation Objects

#### Managing Memory in Operation Objects

避免将数据与线程关联

保留对Operation对象的引用

#### Handling Errors and Exceptions

## Determining an Appropriate Scope for Operation Objects

寻找线程数量和每一个线程任务量之间的平衡，如果有很多的Operation，应该分批添加到Queue中以避免过度消耗内存

## Executing Operations

#### Adding Operations to an Operation Queue

添加任务的方式

* \[aQueue addOperation:anOp\]
* \[aQueue addOperations:anArrayOfOps waitUntilFinished:NO\]
* \[aQueue addOperationWithBlock:^{}\];

线性Operation Queue通过依赖确保顺序

GCD线性队列顺序是先进先出

#### Executing Operations Manually

```
手动执行Operation时应该调用start而不是main，因为前者会进行安全检查并发送KVO通知
```

#### Canceling Operations

```
\[NSOperation cancel\]

\[queue cancelAllOperations\]
```

#### Waiting for Operations to Finish

```
\[NSOperation waitUntilFinished\]

\[NSOperationQueue waitUntilAllOperationsAreFinished\]
```

#### Suspending and Resuming Queues



