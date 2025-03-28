```
@timed
```

Une macro pour exécuter une expression et retourner la valeur de l'expression, le temps écoulé en secondes, le total des octets alloués, le temps de collecte des ordures, un objet avec divers compteurs d'allocation mémoire, le temps de compilation en secondes et le temps de recompilation en secondes. Tout conflit de verrouillage où un [`ReentrantLock`](@ref) a dû attendre est affiché sous forme de compte.

Dans certains cas, le système examinera l'expression `@timed` et compilera une partie du code appelé avant que l'exécution de l'expression de niveau supérieur ne commence. Lorsque cela se produit, une partie du temps de compilation ne sera pas comptabilisée. Pour inclure ce temps, vous pouvez exécuter `@timed @eval ...`.

Voir aussi [`@time`](@ref), [`@timev`](@ref), [`@elapsed`](@ref), [`@allocated`](@ref), [`@allocations`](@ref) et [`@lock_conflicts`](@ref).

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
    Le type de retour de cette macro a été changé de `Tuple` à `NamedTuple` dans Julia 1.5.


!!! compat "Julia 1.11"
    Les champs `lock_conflicts`, `compile_time` et `recompile_time` ont été ajoutés dans Julia 1.11.

