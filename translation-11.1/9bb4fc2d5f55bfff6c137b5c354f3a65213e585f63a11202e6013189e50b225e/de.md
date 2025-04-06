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

Die einfachste korrekte Verwendung von [`schedule`](@ref) ist bei einer `Task`, die noch nicht gestartet (geplant) ist. Es ist jedoch möglich, `4d61726b646f776e2e436f64652822222c20227363686564756c652229_40726566` und [`wait`](@ref) als sehr grundlegenden Baustein zum Konstruieren von Synchronisationsschnittstellen zu verwenden. Eine entscheidende Vorbedingung für den Aufruf von `schedule(task)` ist, dass der Aufrufer die `task` "besitzen" muss; d.h., er muss wissen, dass der Aufruf von `wait` in der gegebenen `task` an den Stellen erfolgt, die dem Code bekannt sind, der `schedule(task)` aufruft. Eine Strategie zur Sicherstellung dieser Vorbedingung ist die Verwendung von Atomics, wie im folgenden Beispiel demonstriert:

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

`OneWayEvent` ermöglicht es einer Aufgabe, auf die `notify` einer anderen Aufgabe zu `warten`. Es handelt sich um eine eingeschränkte Kommunikationsschnittstelle, da `wait` nur einmal von einer einzelnen Aufgabe verwendet werden kann (beachten Sie die nicht-atomare Zuweisung von `ev.task`).

In diesem Beispiel darf `notify(ev::OneWayEvent)` `schedule(ev.task)` nur dann aufrufen, wenn *es* den Zustand von `OWE_WAITING` auf `OWE_NOTIFYING` ändert. Dies lässt uns wissen, dass die Aufgabe, die `wait(ev::OneWayEvent)` ausführt, sich jetzt im `ok`-Zweig befindet und dass es keine anderen Aufgaben geben kann, die versuchen, `schedule(ev.task)` aufzurufen, da ihr `@atomicreplace(ev.state, state => OWE_NOTIFYING)` fehlschlagen wird.
