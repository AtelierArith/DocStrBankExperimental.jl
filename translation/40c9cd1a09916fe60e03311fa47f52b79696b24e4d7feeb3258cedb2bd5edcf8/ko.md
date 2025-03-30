```
remotecall_wait(f, id::Integer, args...; kwargs...)
```

지정된 작업자 ID `id`에 대해 하나의 메시지로 더 빠른 `wait(remotecall(...))`을 수행합니다. 키워드 인수는 있는 경우 `f`로 전달됩니다.

또한 [`wait`](@ref) 및 [`remotecall`](@ref)를 참조하십시오.
