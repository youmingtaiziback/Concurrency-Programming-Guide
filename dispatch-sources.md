# Dispatch Sources

## About Dispatch Sources

GCD支持的dispatch source类型

* timer
* singal：a UNIX signal arrives
* Descriptor：file- and socket-based operations
* Process
* Mach port
* Custom

Dispatch sources异步处理系统相关的事件。配置dispatch source时需要提供事件、queueu、处理代码

dispatch source能够连续的处理事件

当前一个事件未处理时，如果来了新的事件，则更新旧的状态

## Creating Dispatch Sources

创建dispatch source

* dispatch\_source\_create 
* 配置dispatch source：添加事物处理器或者timer信息
* 添加取消逻辑（可选）
* dispatch\_resume

#### Writing and Installing an Event Handler

dispatch\_source\_set\_event\_handler 

当一个新的事件到来时，如果处理器处于准备状态，则合并两个事件。如果处理器已经运行，就等处理完旧的事件再处理新的事件

#### Installing a Cancellation Handler

#### Changing the Target Queue

#### Associating Custom Data with a Dispatch Source

#### Memory Management for Dispatch Sources

## Dispatch Source Examples

## Canceling a Dispatch Source

## Suspending and Resuming Dispatch Sources

## 



