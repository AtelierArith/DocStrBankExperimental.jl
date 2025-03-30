```
remote_do(f, pool::AbstractWorkerPool, args...; kwargs...) -> nothing
```

[`WorkerPool`](@ref) varyantı `remote_do(f, pid, ....)`'dir. `pool`'dan boş bir işçi bekler ve alır ve üzerinde bir `remote_do` gerçekleştirir.
