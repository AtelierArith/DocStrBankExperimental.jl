```
div(x, y)
÷(x, y)
```

El cociente de la división euclidiana (entera). Generalmente equivalente a una operación matemática x/y sin una parte fraccionaria.

Véase también: [`cld`](@ref), [`fld`](@ref), [`rem`](@ref), [`divrem`](@ref).

# Ejemplos

```jldoctest
julia> 9 ÷ 4
2

julia> -5 ÷ 3
-1

julia> 5.0 ÷ 2
2.0

julia> div.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 -1  -1  -1  0  0  0  0  0  1  1  1
```
