```
remotecall_wait(f, id::Integer, args...; kwargs...)
```

在由工作者 ID `id` 指定的 `Worker` 上以单个消息执行更快的 `wait(remotecall(...))`。关键字参数（如果有）将传递给 `f`。

另见 [`wait`](@ref) 和 [`remotecall`](@ref)。
