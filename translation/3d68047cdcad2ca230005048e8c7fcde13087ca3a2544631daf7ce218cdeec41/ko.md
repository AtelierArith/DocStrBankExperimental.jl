```
ReentrantLock()
```

동기화를 위한 재진입 잠금을 생성합니다 [`Task`](@ref)s. 동일한 작업은 필요에 따라 잠금을 여러 번 획득할 수 있습니다(이것이 이름의 "Reentrant" 부분이 의미하는 바입니다). 각 [`lock`](@ref)는 [`unlock`](@ref)과 쌍을 이루어야 합니다.

`lock`을 호출하면 해당 스레드에서 최종화기의 실행이 해당 `unlock`이 호출될 때까지 금지됩니다. 아래에 설명된 표준 잠금 패턴의 사용은 자연스럽게 지원되어야 하지만, 시도/잠금 순서를 뒤집거나 시도 블록을 완전히 누락하는 것(예: 잠금을 유지한 채로 반환하려고 시도하는 것)에 주의해야 합니다:

이것은 잠금/해제 호출에 대한 획득/해제 메모리 순서를 제공합니다.

```
lock(l)
try
    <atomic work>
finally
    unlock(l)
end
```

[`!islocked(lck::ReentrantLock)`](@ref islocked) 조건이 참이면, [`trylock(lck)`](@ref trylock)는 "동시에" 잠금을 보유하려고 시도하는 다른 작업이 없는 한 성공합니다.
