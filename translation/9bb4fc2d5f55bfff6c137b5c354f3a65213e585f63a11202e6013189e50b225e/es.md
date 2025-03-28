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

El uso correcto más fácil de [`schedule`](@ref) es en una `Tarea` que aún no ha comenzado (programada). Sin embargo, es posible usar `4d61726b646f776e2e436f64652822222c20227363686564756c652229_40726566` y [`wait`](@ref) como un bloque de construcción de muy bajo nivel para construir interfaces de sincronización. Una condición previa crucial para llamar a `schedule(task)` es que el llamador debe "poseer" la `tarea`; es decir, debe saber que la llamada a `wait` en la `tarea` dada está ocurriendo en las ubicaciones conocidas por el código que llama a `schedule(task)`. Una estrategia para asegurar tal condición previa es usar atómicos, como se demuestra en el siguiente ejemplo:

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

`OneWayEvent` permite que una tarea `espere` la `notificación` de otra tarea. Es una interfaz de comunicación limitada ya que `wait` solo puede ser utilizado una vez desde una única tarea (nota la asignación no atómica de `ev.task`)

En este ejemplo, `notify(ev::OneWayEvent)` puede llamar a `schedule(ev.task)` si y solo si *modifica* el estado de `OWE_WAITING` a `OWE_NOTIFYING`. Esto nos permite saber que la tarea que ejecuta `wait(ev::OneWayEvent)` está ahora en la rama `ok` y que no puede haber otras tareas que intenten `schedule(ev.task)` ya que su `@atomicreplace(ev.state, state => OWE_NOTIFYING)` fallará.
