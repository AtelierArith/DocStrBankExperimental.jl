```
TaskLocalRNG
```

`TaskLocalRNG`는 스레드가 아닌 작업에 로컬한 상태를 가지고 있습니다. 작업 생성 시 부모 작업의 상태에서 시드가 설정되지만, 부모의 RNG 상태는 진행되지 않습니다.

장점으로는 `TaskLocalRNG`가 매우 빠르며, 스케줄러 결정과 무관하게 재현 가능한 다중 스레드 시뮬레이션을 허용합니다(경쟁 조건을 제외하고). 작업 생성에 대한 결정에 스레드 수가 사용되지 않는 한, 시뮬레이션 결과는 사용 가능한 스레드/CPU 수와도 독립적입니다. 난수 스트림은 하드웨어의 세부 사항에 의존하지 않아야 하며, 엔디안 및 가능성 있는 워드 크기까지 포함됩니다.

`current_task()`에서 반환된 작업이 아닌 다른 작업의 RNG를 사용하거나 시드하는 것은 정의되지 않은 동작입니다: 대부분의 경우 작동하지만, 때때로 조용히 실패할 수 있습니다.

[`seed!`](@ref)로 `TaskLocalRNG()`를 시드할 때, 전달된 시드는(있는 경우) 어떤 정수도 될 수 있습니다.

!!! compat "Julia 1.11"
    음수 정수 시드로 `TaskLocalRNG()`를 시드하는 것은 최소한 Julia 1.11이 필요합니다.


!!! compat "Julia 1.10"
    Julia 1.10부터 작업 생성이 더 이상 부모 작업의 RNG 상태를 진행하지 않습니다.

