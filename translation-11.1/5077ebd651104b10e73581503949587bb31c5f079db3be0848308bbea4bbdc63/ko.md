```
@task
```

표현식을 실행하지 않고 [`Task`](@ref)로 감싸고, [`Task`](@ref)를 반환합니다. 이는 작업을 생성할 뿐이며 실행하지는 않습니다.

!!! 경고     기본적으로 작업은 sticky 비트가 true로 설정됩니다 `t.sticky`. 이는 [`@async`](@ref)의 역사적 기본값을 모델링합니다. Sticky 작업은 처음 예약된 작업 스레드에서만 실행될 수 있으며, 예약될 때 예약된 작업을 sticky로 만듭니다. [`Threads.@spawn`](@ref)와 동일한 동작을 얻으려면 sticky 비트를 수동으로 false로 설정하십시오.

# 예제

```jldoctest
julia> a1() = sum(i for i in 1:1000);

julia> b = @task a1();

julia> istaskstarted(b)
false

julia> schedule(b);

julia> yield();

julia> istaskdone(b)
true
```
