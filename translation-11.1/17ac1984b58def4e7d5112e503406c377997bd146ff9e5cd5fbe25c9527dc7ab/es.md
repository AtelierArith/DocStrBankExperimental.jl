```
remote_do(f, pool::AbstractWorkerPool, args...; kwargs...) -> nothing
```

Variante de [`WorkerPool`](@ref) de `remote_do(f, pid, ....)`. Espera y toma un trabajador libre de `pool` y realiza un `remote_do` en él.
