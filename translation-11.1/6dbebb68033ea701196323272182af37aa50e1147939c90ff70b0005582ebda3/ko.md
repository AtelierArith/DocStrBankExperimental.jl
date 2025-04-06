```
lock(f::Function, lock)
```

`lock`을 획득하고, `lock`이 유지되는 동안 `f`를 실행하며, `f`가 반환되면 `lock`을 해제합니다. 만약 `lock`이 다른 작업/스레드에 의해 이미 잠겨 있다면, 사용 가능해질 때까지 기다립니다.

이 함수가 반환되면 `lock`이 해제되므로, 호출자는 `unlock`을 시도해서는 안 됩니다.

참고: [`@lock`](@ref).

!!! compat "Julia 1.7"
    두 번째 인수로 [`Channel`](@ref)를 사용하는 것은 Julia 1.7 이상이 필요합니다.

