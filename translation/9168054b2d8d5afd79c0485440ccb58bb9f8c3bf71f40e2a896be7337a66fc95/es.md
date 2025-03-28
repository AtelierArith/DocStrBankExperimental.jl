```
@timed
```

Una macro para ejecutar una expresión y devolver el valor de la expresión, el tiempo transcurrido en segundos, el total de bytes asignados, el tiempo de recolección de basura, un objeto con varios contadores de asignación de memoria, el tiempo de compilación en segundos y el tiempo de recompilación en segundos. Cualquier conflicto de bloqueo donde un [`ReentrantLock`](@ref) tuvo que esperar se muestra como un conteo.

En algunos casos, el sistema mirará dentro de la expresión `@timed` y compilará parte del código llamado antes de que comience la ejecución de la expresión de nivel superior. Cuando eso sucede, parte del tiempo de compilación no se contará. Para incluir este tiempo, puedes ejecutar `@timed @eval ...`.

Ver también [`@time`](@ref), [`@timev`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref), [`@allocations`](@ref) y [`@lock_conflicts`](@ref).

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
    El tipo de retorno de esta macro se cambió de `Tuple` a `NamedTuple` en Julia 1.5.


!!! compat "Julia 1.11"
    Los campos `lock_conflicts`, `compile_time` y `recompile_time` se añadieron en Julia 1.11.

