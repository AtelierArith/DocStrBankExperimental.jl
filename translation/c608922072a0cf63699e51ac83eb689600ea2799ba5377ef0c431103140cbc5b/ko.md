```
remotecall_fetch(f, id::Integer, args...; kwargs...)
```

`fetch(remotecall(...))`를 한 메시지에서 수행합니다. 키워드 인수는 있을 경우 `f`로 전달됩니다. 모든 원격 예외는 [`RemoteException`](@ref)으로 캡처되어 던져집니다.

자세한 내용은 [`fetch`](@ref) 및 [`remotecall`](@ref)를 참조하세요.

# 예제

```julia-repl
$ julia -p 2

julia> remotecall_fetch(sqrt, 2, 4)
2.0

julia> remotecall_fetch(sqrt, 2, -4)
ERROR: On worker 2:
DomainError with -4.0:
sqrt는 음의 실수 인수로 호출되었지만 복소수 인수로 호출될 경우에만 복소수 결과를 반환합니다. sqrt(Complex(x))를 시도해 보세요.
...
```
