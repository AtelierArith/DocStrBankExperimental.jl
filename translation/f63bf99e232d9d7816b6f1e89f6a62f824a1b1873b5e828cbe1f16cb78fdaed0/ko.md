```
trymkpidlock([f::Function], at::String, [pid::Cint]; kwopts...)
trymkpidlock(at::String, proc::Process; kwopts...)
```

`mkpidlock`과 유사하지만, 파일이 이미 잠겨 있는 경우 대기하는 대신 `false`를 반환합니다.

!!! compat "Julia 1.10"
    이 함수는 최소한 Julia 1.10이 필요합니다.

