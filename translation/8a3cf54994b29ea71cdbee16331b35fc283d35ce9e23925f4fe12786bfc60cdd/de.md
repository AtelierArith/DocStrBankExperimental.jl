```
@showtime expr
```

Wie `@time`, aber druckt auch den auszuwertenden Ausdruck zur Referenz.

!!! compat "Julia 1.8"
    Dieses Makro wurde in Julia 1.8 hinzugefügt.


Siehe auch [`@time`](@ref).

```julia-repl
julia> @showtime sleep(1)
sleep(1): 1.002164 Sekunden (4 Zuweisungen: 128 Bytes)
```
