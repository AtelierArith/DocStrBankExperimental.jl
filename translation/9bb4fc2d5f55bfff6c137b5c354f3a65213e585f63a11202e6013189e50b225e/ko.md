# Tasks

```@docs
Core.Task
Base.@task
Base.@async
Base.asyncmap
Base.asyncmap!
Base.current_task
Base.istaskdone
Base.istaskstarted
Base.istaskfailed
Base.task_local_storage(::Any)
Base.task_local_storage(::Any, ::Any)
Base.task_local_storage(::Function, ::Any, ::Any)
```

## Scheduling

```@docs
Base.yield
Base.yieldto
Base.sleep
Base.schedule
```

## [Synchronization](@id lib-task-sync)

```@docs
Base.errormonitor
Base.@sync
Base.wait
Base.fetch(t::Task)
Base.fetch(x::Any)
Base.timedwait

Base.Condition
Base.Threads.Condition
Base.Threads.Event
Base.notify
Base.reset(::Base.Threads.Event)

Base.Semaphore
Base.acquire
Base.release

Base.AbstractLock
Base.lock
Base.unlock
Base.trylock
Base.islocked
Base.ReentrantLock
Base.@lock
Base.Lockable
```

## Channels

```@docs
Base.AbstractChannel
Base.Channel
Base.Channel(::Function)
Base.put!(::Channel, ::Any)
Base.take!(::Channel)
Base.isready(::Channel)
Base.fetch(::Channel)
Base.close(::Channel)
Base.bind(c::Channel, task::Task)
```

## [Low-level synchronization using `schedule` and `wait`](@id low-level-schedule-wait)

[`schedule`](@ref)의 가장 쉬운 올바른 사용법은 아직 시작되지 않은 (예정된) `Task`에서 사용하는 것입니다. 그러나 `4d61726b646f776e2e436f64652822222c20227363686564756c652229_40726566`와 [`wait`](@ref)를 동기화 인터페이스를 구성하는 매우 저수준의 빌딩 블록으로 사용할 수 있습니다. `schedule(task)`를 호출하기 위한 중요한 전제 조건은 호출자가 `task`를 "소유"해야 한다는 것입니다. 즉, 주어진 `task`에서 `wait` 호출이 `schedule(task)`를 호출하는 코드에서 알고 있는 위치에서 발생하고 있어야 합니다. 이러한 전제 조건을 보장하기 위한 한 가지 전략은 다음 예제에서 보여준 것처럼 원자성을 사용하는 것입니다.

```jldoctest
@enum OWEState begin
    OWE_EMPTY
    OWE_WAITING
    OWE_NOTIFYING
end

mutable struct OneWayEvent
    @atomic state::OWEState
    task::Task
    OneWayEvent() = new(OWE_EMPTY)
end

function Base.notify(ev::OneWayEvent)
    state = @atomic ev.state
    while state !== OWE_NOTIFYING
        # Spin until we successfully update the state to OWE_NOTIFYING:
        state, ok = @atomicreplace(ev.state, state => OWE_NOTIFYING)
        if ok
            if state == OWE_WAITING
                # OWE_WAITING -> OWE_NOTIFYING transition means that the waiter task is
                # already waiting or about to call `wait`. The notifier task must wake up
                # the waiter task.
                schedule(ev.task)
            else
                @assert state == OWE_EMPTY
                # Since we are assuming that there is only one notifier task (for
                # simplicity), we know that the other possible case here is OWE_EMPTY.
                # We do not need to do anything because we know that the waiter task has
                # not called `wait(ev::OneWayEvent)` yet.
            end
            break
        end
    end
    return
end

function Base.wait(ev::OneWayEvent)
    ev.task = current_task()
    state, ok = @atomicreplace(ev.state, OWE_EMPTY => OWE_WAITING)
    if ok
        # OWE_EMPTY -> OWE_WAITING transition means that the notifier task is guaranteed to
        # invoke OWE_WAITING -> OWE_NOTIFYING transition.  The waiter task must call
        # `wait()` immediately.  In particular, it MUST NOT invoke any function that may
        # yield to the scheduler at this point in code.
        wait()
    else
        @assert state == OWE_NOTIFYING
        # Otherwise, the `state` must have already been moved to OWE_NOTIFYING by the
        # notifier task.
    end
    return
end

ev = OneWayEvent()
@sync begin
    @async begin
        wait(ev)
        println("done")
    end
    println("notifying...")
    notify(ev)
end

# output
notifying...
done
```

`OneWayEvent`는 한 작업이 다른 작업의 `notify`를 `wait`할 수 있게 해줍니다. 이는 `wait`가 단일 작업에서 한 번만 사용될 수 있기 때문에 제한된 통신 인터페이스입니다 (비원자적 할당인 `ev.task`에 유의하세요).

이 예제에서 `notify(ev::OneWayEvent)`는 *그것*이 상태를 `OWE_WAITING`에서 `OWE_NOTIFYING`으로 수정하는 경우에만 `schedule(ev.task)`를 호출할 수 있습니다. 이는 `wait(ev::OneWayEvent)`를 실행하는 작업이 이제 `ok` 분기에 있으며, 다른 작업이 `schedule(ev.task)`를 시도할 수 없음을 알려줍니다. 왜냐하면 그들의 `@atomicreplace(ev.state, state => OWE_NOTIFYING)`가 실패할 것이기 때문입니다.
