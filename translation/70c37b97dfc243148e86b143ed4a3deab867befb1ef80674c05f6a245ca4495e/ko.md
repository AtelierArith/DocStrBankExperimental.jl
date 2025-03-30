```
stacktrace([trace::Vector{Ptr{Cvoid}},] [c_funcs::Bool=false]) -> StackTrace
```

스택 프레임의 벡터 형태로 스택 트레이스를 반환합니다. (기본적으로 stacktrace는 C 함수를 반환하지 않지만, 이를 활성화할 수 있습니다.) trace를 지정하지 않고 호출하면, `stacktrace`는 먼저 `backtrace`를 호출합니다.
