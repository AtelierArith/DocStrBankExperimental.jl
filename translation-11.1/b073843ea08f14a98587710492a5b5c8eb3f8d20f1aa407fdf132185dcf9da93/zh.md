```
remotecall(f, pool::AbstractWorkerPool, args...; kwargs...) -> Future
```

[`WorkerPool`](@ref) 变体的 `remotecall(f, pid, ....)`。等待并从 `pool` 中获取一个空闲的工作者，并在其上执行 `remotecall`。

# 示例

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> f = remotecall(maximum, wp, A)
Future(2, 1, 6, nothing)
```

在这个例子中，任务在 pid 2 上运行，从 pid 1 调用。
