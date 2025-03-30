```
remotecall_fetch(f, pool::AbstractWorkerPool, args...; kwargs...) -> sonuç
```

[`WorkerPool`](@ref) varyantı `remotecall_fetch(f, pid, ....)`. `pool`'dan boş bir işçi bekler ve alır ve üzerinde `remotecall_fetch` gerçekleştirir.

# Örnekler

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> remotecall_fetch(maximum, wp, A)
0.9995177101692958
```
