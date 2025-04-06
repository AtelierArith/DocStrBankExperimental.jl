```
@task
```

Wickeln Sie einen Ausdruck in eine [`Task`](@ref) ein, ohne ihn auszuführen, und geben Sie die [`Task`](@ref) zurück. Dies erstellt nur eine Aufgabe und führt sie nicht aus.

!!! warning
    Standardmäßig haben Aufgaben das Sticky-Bit auf true `t.sticky` gesetzt. Dies modelliert das historische Standardverhalten für [`@async`](@ref). Sticky-Aufgaben können nur auf dem Worker-Thread ausgeführt werden, auf dem sie zuerst geplant wurden, und beim Planen wird die Aufgabe, von der sie geplant wurden, sticky. Um das Verhalten von [`Threads.@spawn`](@ref) zu erhalten, setzen Sie das Sticky-Bit manuell auf `false`.


# Beispiele

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
