```
remotecall(f, pool::AbstractWorkerPool, args...; kwargs...) -> Future
```

[`WorkerPool`](@ref) varyantı `remotecall(f, pid, ....)`. `pool`'dan boş bir işçi bekleyin ve üzerinde `remotecall` gerçekleştirin.

# Örnekler

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> f = remotecall(maximum, wp, A)
Future(2, 1, 6, nothing)
```

Bu örnekte, görev pid 2 üzerinde çalıştı, pid 1'den çağrıldı. ```
