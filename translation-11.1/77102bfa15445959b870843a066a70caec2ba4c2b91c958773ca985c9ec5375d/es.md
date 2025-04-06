```
lmul!(a::Number, B::AbstractArray)
```

Escala un array `B` por un escalar `a` sobrescribiendo `B` en su lugar. Usa [`rmul!`](@ref) para multiplicar el escalar desde la derecha. La operación de escalado respeta la semántica de la multiplicación [`*`](@ref) entre `a` y un elemento de `B`. En particular, esto también se aplica a la multiplicación que involucra números no finitos como `NaN` y `±Inf`.

!!! compat "Julia 1.1"
    Antes de Julia 1.1, las entradas `NaN` y `±Inf` en `B` se trataban de manera inconsistente.


# Ejemplos

```jldoctest
julia> B = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> lmul!(2, B)
2×2 Matrix{Int64}:
 2  4
 6  8

julia> lmul!(0.0, [Inf])
1-element Vector{Float64}:
 NaN
```
