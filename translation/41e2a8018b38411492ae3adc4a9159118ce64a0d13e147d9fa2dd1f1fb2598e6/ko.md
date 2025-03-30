```
isready(rr::Future)
```

[`Future`](@ref)에 값이 저장되어 있는지 확인합니다.

인수 `Future`가 다른 노드에 의해 소유되는 경우, 이 호출은 답변을 기다리기 위해 차단됩니다. 대신 `rr`을 별도의 작업에서 기다리거나 로컬 [`Channel`](@ref)를 프록시로 사용하는 것이 좋습니다:

```julia
p = 1
f = Future(p)
errormonitor(@async put!(f, remotecall_fetch(long_computation, p)))
isready(f)  # 차단되지 않음
```
