```
remotecall_fetch(f, pool::AbstractWorkerPool, args...; kwargs...) -> result
```

[`WorkerPool`](@ref) variante de `remotecall_fetch(f, pid, ....)`. Attend et prend un travailleur libre de `pool` et effectue un `remotecall_fetch` dessus.

# Exemples

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> remotecall_fetch(maximum, wp, A)
0.9995177101692958
```
