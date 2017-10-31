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

## Defining a Custom Operation Object

## Customizing the Execution Behavior of an Operation Object

## Tips for Implementing Operation Objects

## Determining an Appropriate Scope for Operation Objects

## Executing Operations

## 



