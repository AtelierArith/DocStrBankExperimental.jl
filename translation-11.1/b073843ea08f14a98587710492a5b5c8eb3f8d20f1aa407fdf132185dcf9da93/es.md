```
remotecall(f, pool::AbstractWorkerPool, args...; kwargs...) -> Future
```

[`WorkerPool`](@ref) variante de `remotecall(f, pid, ....)`. Espera y toma un trabajador libre de `pool` y realiza un `remotecall` en él.

# Ejemplos

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> f = remotecall(maximum, wp, A)
Future(2, 1, 6, nothing)
```

En este ejemplo, la tarea se ejecutó en pid 2, llamada desde pid 1.
