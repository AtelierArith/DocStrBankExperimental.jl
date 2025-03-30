```
Threads.foreach(f, channel::Channel;
                schedule::Threads.AbstractSchedule=Threads.FairSchedule(),
                ntasks=Threads.threadpoolsize())
```

`foreach(f, channel)`와 유사하지만, `channel`에 대한 반복과 `f`에 대한 호출이 `Threads.@spawn`에 의해 생성된 `ntasks` 작업에 분산됩니다. 이 함수는 내부적으로 생성된 모든 작업이 완료될 때까지 기다린 후 반환됩니다.

`schedule isa FairSchedule`인 경우, `Threads.foreach`는 Julia의 스케줄러가 스레드 간에 작업 항목을 보다 자유롭게 로드 밸런싱할 수 있도록 작업을 생성하려고 시도합니다. 이 접근 방식은 일반적으로 항목당 오버헤드가 더 높지만, 다른 멀티스레드 작업과 동시에 수행할 때 `StaticSchedule`보다 더 나은 성능을 발휘할 수 있습니다.

`schedule isa StaticSchedule`인 경우, `Threads.foreach`는 `FairSchedule`보다 항목당 오버헤드가 낮은 방식으로 작업을 생성하지만, 로드 밸런싱에는 덜 적합합니다. 따라서 이 접근 방식은 세밀하고 균일한 작업에 더 적합할 수 있지만, 다른 멀티스레드 작업과 동시에 수행할 때 `FairSchedule`보다 성능이 떨어질 수 있습니다.

# 예제

```julia-repl
julia> n = 20

julia> c = Channel{Int}(ch -> foreach(i -> put!(ch, i), 1:n), 1)

julia> d = Channel{Int}(n) do ch
           f = i -> put!(ch, i^2)
           Threads.foreach(f, c)
       end

julia> collect(d)
collect(d) = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100, 121, 144, 169, 196, 225, 256, 289, 324, 361, 400]
```

!!! compat "Julia 1.6"
    이 함수는 Julia 1.6 이상이 필요합니다.

