```
Event([autoreset=false])
```

레벨 트리거 이벤트 소스를 생성합니다. `Event`에서 [`wait`](@ref)를 호출하는 작업은 중단되고 대기열에 추가되며, `Event`에서 [`notify`](@ref)가 호출될 때까지 대기합니다. `notify`가 호출된 후, `Event`는 신호 상태를 유지하며, `reset`이 호출될 때까지 작업이 대기할 때 더 이상 차단되지 않습니다.

`autoreset`이 true인 경우, `notify` 호출당 최대 하나의 작업만 `wait`에서 해제됩니다.

이는 notify/wait에 대한 획득 및 해제 메모리 순서를 제공합니다.

!!! compat "Julia 1.1"
    이 기능은 최소한 Julia 1.1이 필요합니다.


!!! compat "Julia 1.8"
    `autoreset` 기능 및 메모리 순서 보장은 최소한 Julia 1.8이 필요합니다.

