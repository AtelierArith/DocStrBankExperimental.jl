```
close(c::Channel[, excp::Exception])
```

채널을 닫습니다. 예외(`excp`로 선택적으로 제공됨)는 다음에 의해 발생합니다:

  * 닫힌 채널에서 [`put!`](@ref).
  * 비어 있고 닫힌 채널에서 [`take!`](@ref) 및 [`fetch`](@ref).
