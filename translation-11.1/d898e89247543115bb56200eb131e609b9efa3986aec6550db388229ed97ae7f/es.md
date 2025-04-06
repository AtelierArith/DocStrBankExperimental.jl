```
>>(x, n)
```

Operador de desplazamiento a la derecha, `x >> n`. Para `n >= 0`, el resultado es `x` desplazado a la derecha por `n` bits, llenando con `0`s si `x >= 0`, `1`s si `x < 0`, preservando el signo de `x`. Esto es equivalente a `fld(x, 2^n)`. Para `n < 0`, esto es equivalente a `x << -n`.

# Ejemplos

```jldoctest
julia> Int8(13) >> 2
3

julia> bitstring(Int8(13))
"00001101"

julia> bitstring(Int8(3))
"00000011"

julia> Int8(-14) >> 2
-4

julia> bitstring(Int8(-14))
"11110010"

julia> bitstring(Int8(-4))
"11111100"
```

Ver también [`>>>`](@ref), [`<<`](@ref).
