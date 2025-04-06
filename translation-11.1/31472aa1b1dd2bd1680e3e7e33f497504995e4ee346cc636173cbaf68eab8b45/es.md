```
x || y
```

OR boolean de cortocircuito.

Véase también: [`|`](@ref), [`xor`](@ref), [`&&`](@ref).

# Ejemplos

```jldoctest
julia> pi < 3 || ℯ < 3
true

julia> false || true || println("¡ninguno es verdadero!")
true
```
