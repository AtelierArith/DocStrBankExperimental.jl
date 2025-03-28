```
Task(func)
```

Erstellen Sie eine `Task` (d.h. Coroutine), um die gegebene Funktion `func` auszuführen (die ohne Argumente aufrufbar sein muss). Die Aufgabe endet, wenn diese Funktion zurückkehrt. Die Aufgabe wird im "Weltalter" des Elternteils zur Zeit der Konstruktion ausgeführt, wenn sie [`schedule`](@ref)d wird.

!!! warning
    Standardmäßig haben Aufgaben das Sticky-Bit auf true `t.sticky` gesetzt. Dies modelliert das historische Standardverhalten für [`@async`](@ref). Sticky-Aufgaben können nur auf dem Worker-Thread ausgeführt werden, auf dem sie zuerst geplant wurden, und wenn sie geplant werden, machen sie die Aufgabe, von der sie geplant wurden, sticky. Um das Verhalten von [`Threads.@spawn`](@ref) zu erhalten, setzen Sie das Sticky-Bit manuell auf `false`.


# Beispiele

```jldoctest
julia> a() = sum(i for i in 1:1000);

julia> b = Task(a);
```

In diesem Beispiel ist `b` eine ausführbare `Task`, die noch nicht gestartet wurde.
