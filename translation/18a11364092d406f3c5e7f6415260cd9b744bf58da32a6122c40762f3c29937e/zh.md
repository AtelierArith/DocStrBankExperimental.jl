```
systemsleep(s::Real)
```

暂停执行 `s` 秒。此函数不会让出 Julia 的调度器，因此会在睡眠时间内阻塞其运行的 Julia 线程。

另见 [`sleep`](@ref).
