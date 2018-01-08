## 什么是 Subject？
> RxJS Subject 是一种特殊类型的 Observable，它允许将值多播给多个观察者，所以 Subject 是多播的，而普通的 Observables 是单播的(每个已订阅的观察者都拥有 Observable 的独立执行)。多播 Observable 在底层是通过使用 Subject 使得多个观察者可以看见同一个 Observable 执行。

## BehaviorSubject
> Subject 的其中一个变体就是 BehaviorSubject，它有一个“当前值”的概念。它保存了发送给消费者的最新值。并且当有新的观察者订阅时，会立即从 BehaviorSubject 那接收到“当前值”。

## ReplaySubject
> ReplaySubject 类似于 BehaviorSubject，它可以发送旧值给新的订阅者，但它还可以记录 Observable 执行的一部分。ReplaySubject 记录 Observable 执行中的多个值并将其回放给新的订阅者。

## AsyncSubject
> AsyncSubject 是另一个 Subject 变体，只有当 Observable 执行完成时(执行 complete())，它才会将执行的最后一个值发送给观察者。

## Scheduler
> 调度器控制着何时启动 subscription 和何时发送通知。它由三部分组成：
>1. 调度器是一种数据结构。 它知道如何根据优先级或其他标准来存储任务和将任务进行排序。
>1. 调度器是执行上下文。 它表示在何时何地执行任务(举例来说，立即的，或另一种回调函数机制(比如 setTimeout 或 process.nextTick)，或动画帧)。
>1. 调度器有一个(虚拟的)时钟。 调度器功能通过它的 getter 方法 now() 提供了“时间”的概念。在具体调度器上安排的任务将严格遵循该时钟所表示的时间。
>
> 调度器可以让你规定 Observable 在什么样的执行上下文中发送通知给它的观察者。
