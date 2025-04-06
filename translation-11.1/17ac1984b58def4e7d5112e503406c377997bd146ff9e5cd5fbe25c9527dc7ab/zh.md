```
remote_do(f, pool::AbstractWorkerPool, args...; kwargs...) -> nothing
```

[`WorkerPool`](@ref) 变体的 `remote_do(f, pid, ....)`。等待并从 `pool` 中获取一个空闲的工作者，并在其上执行 `remote_do`。
