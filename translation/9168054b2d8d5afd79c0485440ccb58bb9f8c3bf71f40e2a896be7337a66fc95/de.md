```
@timed
```

Eine Makro, um einen Ausdruck auszuführen und den Wert des Ausdrucks, die verstrichene Zeit in Sekunden, die insgesamt zugewiesenen Bytes, die Zeit der Müllsammlung, ein Objekt mit verschiedenen Zählern für die Speicherzuweisung, die Kompilierungszeit in Sekunden und die Rekompilierungszeit in Sekunden zurückzugeben. Alle Sperrkonflikte, bei denen ein [`ReentrantLock`](@ref) warten musste, werden als Zähler angezeigt.

In einigen Fällen wird das System innerhalb des `@timed`-Ausdrucks nachsehen und einen Teil des aufgerufenen Codes vor der Ausführung des obersten Ausdrucks kompilieren. Wenn das passiert, wird einige Kompilierungszeit nicht gezählt. Um diese Zeit einzuschließen, können Sie `@timed @eval ...` ausführen.

Siehe auch [`@time`](@ref), [`@timev`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref), [`@allocations`](@ref) und [`@lock_conflicts`](@ref).

```julia-repl
julia> stats = @timed rand(10^6);

julia> stats.time
0.006634834

julia> stats.bytes
8000256

julia> stats.gctime
0.0055765

julia> propertynames(stats.gcstats)
(:allocd, :malloc, :realloc, :poolalloc, :bigalloc, :freecall, :total_time, :pause, :full_sweep)

julia> stats.gcstats.total_time
5576500

julia> stats.compile_time
0.0

julia> stats.recompile_time
0.0

```

!!! compat "Julia 1.5"
    Der Rückgabetyp dieses Makros wurde in Julia 1.5 von `Tuple` auf `NamedTuple` geändert.


!!! compat "Julia 1.11"
    Die Felder `lock_conflicts`, `compile_time` und `recompile_time` wurden in Julia 1.11 hinzugefügt.

