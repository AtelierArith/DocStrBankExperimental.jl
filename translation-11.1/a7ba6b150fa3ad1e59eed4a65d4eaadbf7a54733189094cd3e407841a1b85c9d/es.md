```
x && y
```

Cortocircuito booleano AND.

Véase también [`&`](@ref), el operador ternario `? :`, y la sección del manual sobre [flujo de control](@ref man-conditional-evaluation).

# Ejemplos

```jldoctest
julia> x = 3;

julia> x > 1 && x < 10 && x isa Int
true

julia> x < 0 && error("se esperaba un x positivo")
false
```
