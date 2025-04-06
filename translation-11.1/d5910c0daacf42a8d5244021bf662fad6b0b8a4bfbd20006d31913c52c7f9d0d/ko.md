```
remotecall_wait(f, pool::AbstractWorkerPool, args...; kwargs...) -> Future
```

[`WorkerPool`](@ref) 변형의 `remotecall_wait(f, pid, ....)`. `pool`에서 자유로운 작업자를 기다리고 가져와서 그 위에서 `remotecall_wait`을 수행합니다.

# 예제

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> f = remotecall_wait(maximum, wp, A)
Future(3, 1, 9, nothing)

julia> fetch(f)
0.9995177101692958
```
