```
remotecall(f, pool::AbstractWorkerPool, args...; kwargs...) -> Future
```

[`WorkerPool`](@ref) Variante von `remotecall(f, pid, ....)`. Warten Sie auf und nehmen Sie einen freien Arbeiter aus `pool` und führen Sie einen `remotecall` darauf aus.

# Beispiele

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> f = remotecall(maximum, wp, A)
Future(2, 1, 6, nothing)
```

In diesem Beispiel wurde die Aufgabe auf pid 2 ausgeführt, aufgerufen von pid 1.
