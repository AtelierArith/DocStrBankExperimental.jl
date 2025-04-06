```
remotecall(f, pool::AbstractWorkerPool, args...; kwargs...) -> Future
```

[`WorkerPool`](@ref) 변형의 `remotecall(f, pid, ....)`. `pool`에서 대기 중인 작업자를 가져와 `remotecall`을 수행합니다.

# 예제

```julia-repl
$ julia -p 3

julia> wp = WorkerPool([2, 3]);

julia> A = rand(3000);

julia> f = remotecall(maximum, wp, A)
Future(2, 1, 6, nothing)
```

이 예제에서 작업은 pid 2에서 실행되었고, pid 1에서 호출되었습니다.
