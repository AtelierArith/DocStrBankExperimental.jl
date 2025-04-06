```
remotecall_wait(f, pool::AbstractWorkerPool, args...; kwargs...) -> Future
```

[`WorkerPool`](@ref) 变体的 `remotecall_wait(f, pid, ....)`。等待并从 `pool` 中获取一个空闲的工作者，并在其上执行 `remotecall_wait`。

# 示例

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> f = remotecall_wait(maximum, wp, A)
Future(3, 1, 9, nothing)

julia> fetch(f)
0.9995177101692958
```
