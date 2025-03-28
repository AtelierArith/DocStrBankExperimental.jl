```
remotecall(f, pool::AbstractWorkerPool, args...; kwargs...) -> Future
```

variante de [`WorkerPool`](@ref) de `remotecall(f, pid, ....)`. Attendez et prenez un travailleur libre de `pool` et effectuez un `remotecall` dessus.

# Exemples

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> f = remotecall(maximum, wp, A)
Future(2, 1, 6, nothing)
```

Dans cet exemple, la tâche a été exécutée sur pid 2, appelée depuis pid 1.
