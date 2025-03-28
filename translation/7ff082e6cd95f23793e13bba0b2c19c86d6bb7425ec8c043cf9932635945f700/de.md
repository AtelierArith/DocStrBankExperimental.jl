```
schedule(t::Task, [val]; error=false)
```

Fügt eine [`Task`](@ref) zur Warteschlange des Planers hinzu. Dies bewirkt, dass die Aufgabe ständig ausgeführt wird, wenn das System ansonsten untätig ist, es sei denn, die Aufgabe führt eine blockierende Operation wie [`wait`](@ref) aus.

Wenn ein zweites Argument `val` bereitgestellt wird, wird es der Aufgabe (über den Rückgabewert von [`yieldto`](@ref)) übergeben, wenn sie erneut ausgeführt wird. Wenn `error` auf `true` gesetzt ist, wird der Wert als Ausnahme in der geweckten Aufgabe ausgelöst.

!!! warning
    Es ist falsch, `schedule` auf einer beliebigen `Task` zu verwenden, die bereits gestartet wurde. Siehe [die API-Referenz](@ref low-level-schedule-wait) für weitere Informationen.


!!! warning
    Standardmäßig haben Aufgaben das Sticky-Bit auf true `t.sticky` gesetzt. Dies modelliert das historische Standardverhalten für [`@async`](@ref). Sticky-Aufgaben können nur auf dem Worker-Thread ausgeführt werden, auf dem sie zuerst geplant wurden, und wenn sie geplant werden, machen sie die Aufgabe, von der sie geplant wurden, sticky. Um das Verhalten von [`Threads.@spawn`](@ref) zu erhalten, setzen Sie das Sticky-Bit manuell auf `false`.


# Beispiele

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
