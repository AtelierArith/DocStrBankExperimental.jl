```
Event([autoreset=false])
```

创建一个级别触发的事件源。调用 [`wait`](@ref) 的任务在 `Event` 上被挂起并排队，直到在 `Event` 上调用 [`notify`](@ref)。在调用 `notify` 后，`Event` 保持在已信号状态，任务在等待它时将不再阻塞，直到调用 `reset`。

如果 `autoreset` 为真，则每次调用 `notify` 时，最多会释放一个任务从 `wait` 中。

这提供了在 notify/wait 上的获取和释放内存顺序。

!!! compat "Julia 1.1"
    此功能至少需要 Julia 1.1。


!!! compat "Julia 1.8"
    `autoreset` 功能和内存顺序保证至少需要 Julia 1.8。

