```
remotecall_wait(f, pool::AbstractWorkerPool, args...; kwargs...) -> Future
```

[`WorkerPool`](@ref) Variante von `remotecall_wait(f, pid, ....)`. Warten Sie auf und nehmen Sie einen freien Arbeiter aus `pool` und führen Sie ein `remotecall_wait` darauf aus.

# Beispiele

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> f = remotecall_wait(maximum, wp, A)
Future(3, 1, 9, nothing)

julia> fetch(f)
0.9995177101692958
```
