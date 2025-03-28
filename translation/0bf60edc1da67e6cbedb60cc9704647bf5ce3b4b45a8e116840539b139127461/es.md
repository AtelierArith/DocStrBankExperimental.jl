```
signbit(x)
```

Devuelve `true` si el valor del signo de `x` es negativo, de lo contrario `false`.

Véase también [`sign`](@ref) y [`copysign`](@ref).

# Ejemplos

```jldoctest
julia> signbit(-4)
true

julia> signbit(5)
false

julia> signbit(5.5)
false

julia> signbit(-4.1)
true
```
