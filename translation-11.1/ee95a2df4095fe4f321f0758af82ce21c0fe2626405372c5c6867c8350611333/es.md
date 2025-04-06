```
ndigits(n::Integer; base::Integer=10, pad::Integer=1)
```

Calcula el número de dígitos en el entero `n` escrito en base `base` (la `base` no debe estar en `[-1, 0, 1]`), opcionalmente rellenado con ceros hasta un tamaño especificado (el resultado nunca será menor que `pad`).

Véase también [`digits`](@ref), [`count_ones`](@ref).

# Ejemplos

```jldoctest
julia> ndigits(0)
1

julia> ndigits(12345)
5

julia> ndigits(1022, base=16)
3

julia> string(1022, base=16)
"3fe"

julia> ndigits(123, pad=5)
5

julia> ndigits(-123)
3
```
