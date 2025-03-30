```
errormonitor(t::Task)
```

작업 `t`가 실패하면 `stderr`에 오류 로그를 출력합니다.

# 예시

```julia-repl
julia> Base._wait(errormonitor(Threads.@spawn error("작업 실패")))
Unhandled Task ERROR: 작업 실패
Stacktrace:
[...]
```
