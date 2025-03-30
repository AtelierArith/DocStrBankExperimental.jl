```
put!(c::Channel, v)
```

将项 `v` 添加到通道 `c`。如果通道已满，则会阻塞。

对于无缓冲通道，直到其他任务执行 [`take!`](@ref) 时才会阻塞。

!!! compat "Julia 1.1"
    当调用 `put!` 时，`v` 现在会通过 [`convert`](@ref) 转换为通道的类型。

