```
schedule(t::Task, [val]; error=false)
```

스케줄러의 큐에 [`Task`](@ref)를 추가합니다. 이는 시스템이 다른 작업을 수행하지 않을 때 작업이 지속적으로 실행되도록 하며, 작업이 [`wait`](@ref)와 같은 차단 작업을 수행하지 않는 한 계속 실행됩니다.

두 번째 인수 `val`이 제공되면, 작업이 다시 실행될 때 ( [`yieldto`](@ref)의 반환 값을 통해) 작업에 전달됩니다. `error`가 `true`인 경우, 값은 깨어난 작업에서 예외로 발생합니다.

!!! warning
    이미 시작된 임의의 `Task`에 대해 `schedule`을 사용하는 것은 잘못된 것입니다. 자세한 내용은 [API 참조](@ref low-level-schedule-wait)를 참조하십시오.


!!! warning
    기본적으로 작업은 `t.sticky`가 true로 설정됩니다. 이는 [`@async`](@ref)의 역사적 기본값을 모델링합니다. 스티키 작업은 처음 스케줄된 작업 스레드에서만 실행될 수 있으며, 스케줄될 때 스케줄된 작업을 스티키로 만듭니다. [`Threads.@spawn`](@ref)과 동일한 동작을 얻으려면 스티키 비트를 수동으로 `false`로 설정하십시오.


# 예제

```jldoctest
julia> a5() = sum(i for i in 1:1000);

julia> b = Task(a5);

julia> istaskstarted(b)
false

julia> schedule(b);

julia> yield();

julia> istaskstarted(b)
true

julia> istaskdone(b)
true
```
