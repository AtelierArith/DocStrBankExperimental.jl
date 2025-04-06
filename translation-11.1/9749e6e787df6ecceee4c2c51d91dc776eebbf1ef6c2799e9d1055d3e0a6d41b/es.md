```
cld(x, y)
```

El entero más pequeño mayor o igual que `x / y`. Equivalente a `div(x, y, RoundUp)`.

Véase también [`div`](@ref), [`fld`](@ref).

# Ejemplos

```jldoctest
julia> cld(5.5, 2.2)
3.0

julia> cld.(-5:5, 3)'
1×11 adjunto(::Vector{Int64}) con el tipo de elemento Int64:
 -1  -1  -1  0  0  0  1  1  1  2  2
```
