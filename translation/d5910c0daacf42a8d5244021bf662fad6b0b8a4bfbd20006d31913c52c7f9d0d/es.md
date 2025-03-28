```
remotecall_wait(f, pool::AbstractWorkerPool, args...; kwargs...) -> Future
```

Variante de [`WorkerPool`](@ref) de `remotecall_wait(f, pid, ....)`. Espera y toma un trabajador libre de `pool` y realiza un `remotecall_wait` en él.

# Ejemplos

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> f = remotecall_wait(maximum, wp, A)
Future(3, 1, 9, nothing)

julia> fetch(f)
0.9995177101692958
```
