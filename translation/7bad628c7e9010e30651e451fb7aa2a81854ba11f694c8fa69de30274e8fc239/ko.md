```
Task(func)
```

주어진 함수 `func` (인수가 없는 호출 가능해야 함)을 실행하기 위해 `Task` (즉, 코루틴)를 생성합니다. 이 함수가 반환되면 작업이 종료됩니다. 작업은 [`schedule`](@ref)d 시 부모의 "세계 나이"에서 실행됩니다.

!!! 경고     기본적으로 작업은 sticky 비트가 true로 설정됩니다 `t.sticky`. 이는 [`@async`](@ref)의 역사적 기본값을 모델링합니다. Sticky 작업은 처음 예약된 작업 스레드에서만 실행될 수 있으며, 예약될 때 예약된 작업을 sticky로 만듭니다. [`Threads.@spawn`](@ref)와 동일한 동작을 얻으려면 sticky 비트를 수동으로 `false`로 설정하십시오.

# 예제

```jldoctest
julia> a() = sum(i for i in 1:1000);

julia> b = Task(a);
```

이 예제에서 `b`는 아직 시작되지 않은 실행 가능한 `Task`입니다.
