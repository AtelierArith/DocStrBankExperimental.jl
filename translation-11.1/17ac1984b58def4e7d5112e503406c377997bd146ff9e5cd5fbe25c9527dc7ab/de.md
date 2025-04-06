```
remote_do(f, pool::AbstractWorkerPool, args...; kwargs...) -> nichts
```

[`WorkerPool`](@ref) Variante von `remote_do(f, pid, ....)`. Warten Sie auf und nehmen Sie einen freien Arbeiter aus `pool` und führen Sie ein `remote_do` darauf aus.
