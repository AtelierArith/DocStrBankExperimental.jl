```
RemoteChannel(pid::Integer=myid())
```

在进程 `pid` 上创建对 `Channel{Any}(1)` 的引用。默认的 `pid` 是当前进程。

```
RemoteChannel(f::Function, pid::Integer=myid())
```

创建对特定大小和类型的远程通道的引用。`f` 是一个函数，当在 `pid` 上执行时，必须返回一个 `AbstractChannel` 的实现。

例如，`RemoteChannel(()->Channel{Int}(10), pid)` 将返回对 `pid` 上类型为 `Int` 和大小为 10 的通道的引用。

默认的 `pid` 是当前进程。
