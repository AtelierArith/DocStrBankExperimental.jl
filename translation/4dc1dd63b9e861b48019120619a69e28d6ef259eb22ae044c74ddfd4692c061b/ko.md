```
remotecall(f, id::Integer, args...; kwargs...) -> Future
```

지정된 프로세스에서 주어진 인수로 함수 `f`를 비동기적으로 호출합니다. [`Future`](@ref)를 반환합니다. 키워드 인수가 있는 경우, `f`에 전달됩니다.
