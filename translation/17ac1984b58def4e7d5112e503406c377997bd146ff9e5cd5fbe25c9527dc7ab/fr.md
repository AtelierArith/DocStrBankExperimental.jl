```
remote_do(f, pool::AbstractWorkerPool, args...; kwargs...) -> rien
```

[`WorkerPool`](@ref) variante de `remote_do(f, pid, ....)`. Attendez et prenez un travailleur libre de `pool` et effectuez un `remote_do` dessus.
