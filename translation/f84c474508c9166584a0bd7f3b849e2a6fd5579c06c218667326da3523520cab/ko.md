```
remotecall_fetch(f, pool::AbstractWorkerPool, args...; kwargs...) -> result
```

[`WorkerPool`](@ref) 변형의 `remotecall_fetch(f, pid, ....)`. `pool`에서 유휴 작업자를 기다리고 가져와서 그 위에서 `remotecall_fetch`를 수행합니다.

# 예제

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> remotecall_fetch(maximum, wp, A)
0.9995177101692958
```
