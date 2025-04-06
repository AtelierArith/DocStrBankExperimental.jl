```
wait([x])
```

阻塞当前任务，直到某个事件发生，具体取决于参数的类型：

  * [`Channel`](@ref)：等待一个值被附加到通道中。
  * [`Condition`](@ref)：等待条件上的[`notify`](@ref)并返回传递给`notify`的`val`参数。等待条件时，还可以传递`first=true`，这会使等待者在`notify`时被放在*第一*位，而不是通常的先进先出行为。
  * `Process`：等待一个进程或进程链退出。可以使用进程的`exitcode`字段来确定成功或失败。
  * [`Task`](@ref)：等待一个`Task`完成。如果任务因异常失败，将抛出`TaskFailedException`（它包装了失败的任务）。
  * [`RawFD`](@ref)：等待文件描述符上的变化（参见`FileWatching`包）。

如果没有传递参数，任务将阻塞一个未定义的时间。任务只能通过显式调用[`schedule`](@ref)或[`yieldto`](@ref)来重新启动。

通常在`while`循环中调用`wait`以确保在继续之前满足等待的条件。
