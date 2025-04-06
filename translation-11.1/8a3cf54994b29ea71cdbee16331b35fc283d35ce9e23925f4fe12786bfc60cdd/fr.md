```
@showtime expr
```

Comme `@time` mais imprime également l'expression évaluée pour référence.

!!! compat "Julia 1.8"
    Ce macro a été ajouté dans Julia 1.8.


Voir aussi [`@time`](@ref).

```julia-repl
julia> @showtime sleep(1)
sleep(1): 1.002164 secondes (4 allocations: 128 octets)
```
