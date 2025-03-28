```
iszero(x)
```

Devuelve `true` si `x == zero(x)`; si `x` es un array, esto verifica si todos los elementos de `x` son cero.

Véase también: [`isone`](@ref), [`isinteger`](@ref), [`isfinite`](@ref), [`isnan`](@ref).

# Ejemplos

```jldoctest
julia> iszero(0.0)
true

julia> iszero([1, 9, 0])
false

julia> iszero([false, 0, 0])
true
```
