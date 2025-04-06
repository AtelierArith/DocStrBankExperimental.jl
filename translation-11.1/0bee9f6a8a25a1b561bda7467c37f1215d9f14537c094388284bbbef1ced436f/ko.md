```
Threads.Condition([lock])
```

스레드 안전한 버전의 [`Base.Condition`](@ref)입니다.

`Threads.Condition`에서 [`wait`](@ref) 또는 [`notify`](@ref)를 호출하려면 먼저 [`lock`](@ref)를 호출해야 합니다. `wait`가 호출되면, 블로킹 동안 잠금이 원자적으로 해제되며, `wait`가 반환되기 전에 다시 획득됩니다. 따라서 `Threads.Condition` `c`의 관용적인 사용은 다음과 같습니다:

```
lock(c)
try
    while !thing_we_are_waiting_for
        wait(c)
    end
finally
    unlock(c)
end
```

!!! compat "Julia 1.2"
    이 기능은 최소한 Julia 1.2가 필요합니다.

