```
@showtime expr
```

Como `@time` pero también imprime la expresión que se está evaluando como referencia.

!!! compat "Julia 1.8"
    Este macro fue añadido en Julia 1.8.


Véase también [`@time`](@ref).

```julia-repl
julia> @showtime sleep(1)
sleep(1): 1.002164 segundos (4 asignaciones: 128 bytes)
```
