```
remotecall_fetch(f, pool::AbstractWorkerPool, args...; kwargs...) -> result
```

[`WorkerPool`](@ref) 变体的 `remotecall_fetch(f, pid, ....)`。等待并从 `pool` 中获取一个空闲的工作者，并在其上执行 `remotecall_fetch`。

# 示例

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> remotecall_fetch(maximum, wp, A)
0.9995177101692958
```
