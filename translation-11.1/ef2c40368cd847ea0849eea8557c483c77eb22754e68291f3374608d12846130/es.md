```
nextpow(a, x)
```

El más pequeño `a^n` no menor que `x`, donde `n` es un entero no negativo. `a` debe ser mayor que 1, y `x` debe ser mayor que 0.

Véase también [`prevpow`](@ref).

# Ejemplos

```jldoctest
julia> nextpow(2, 7)
8

julia> nextpow(2, 9)
16

julia> nextpow(5, 20)
25

julia> nextpow(4, 16)
16
```
