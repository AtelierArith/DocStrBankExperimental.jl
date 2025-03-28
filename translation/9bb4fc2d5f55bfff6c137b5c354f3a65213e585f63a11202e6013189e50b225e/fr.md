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

L'utilisation correcte la plus simple de [`schedule`](@ref) est sur une `Task` qui n'est pas encore commencée (planifiée). Cependant, il est possible d'utiliser `4d61726b646f776e2e436f64652822222c20227363686564756c652229_40726566` et [`wait`](@ref) comme un élément de base très bas niveau pour construire des interfaces de synchronisation. Une condition préalable cruciale pour appeler `schedule(task)` est que l'appelant doit "posséder" la `task` ; c'est-à-dire qu'il doit savoir que l'appel à `wait` dans la `task` donnée se produit aux emplacements connus du code appelant `schedule(task)`. Une stratégie pour garantir une telle condition préalable est d'utiliser des atomiques, comme démontré dans l'exemple suivant :

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

`OneWayEvent` permet à une tâche d'`attendre` la `notification` d'une autre tâche. C'est une interface de communication limitée puisque `attendre` ne peut être utilisé qu'une seule fois par une tâche unique (notez l'assignation non atomique de `ev.task`)

Dans cet exemple, `notify(ev::OneWayEvent)` est autorisé à appeler `schedule(ev.task)` si et seulement si *il* modifie l'état de `OWE_WAITING` à `OWE_NOTIFYING`. Cela nous permet de savoir que la tâche exécutant `wait(ev::OneWayEvent)` est maintenant dans la branche `ok` et qu'il ne peut pas y avoir d'autres tâches qui essaient de `schedule(ev.task)` puisque leur `@atomicreplace(ev.state, state => OWE_NOTIFYING)` échouera.
