```
remotecall_wait(f, pool::AbstractWorkerPool, args...; kwargs...) -> Future
```

[`WorkerPool`](@ref) varyantı `remotecall_wait(f, pid, ....)`. `pool`'dan boş bir işçi bekleyin ve ona `remotecall_wait` gerçekleştirin.

# Örnekler

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> f = remotecall_wait(maximum, wp, A)
Future(3, 1, 9, nothing)

julia> fetch(f)
0.9995177101692958
```
