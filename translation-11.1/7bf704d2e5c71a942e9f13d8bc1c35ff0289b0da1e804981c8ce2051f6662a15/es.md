```
rmul!(A::AbstractArray, b::Number)
```

Escala un arreglo `A` por un escalar `b` sobrescribiendo `A` en su lugar. Usa [`lmul!`](@ref) para multiplicar el escalar desde la izquierda. La operación de escalado respeta la semántica de la multiplicación [`*`](@ref) entre un elemento de `A` y `b`. En particular, esto también se aplica a la multiplicación que involucra números no finitos como `NaN` y `±Inf`.

!!! compat "Julia 1.1"
    Antes de Julia 1.1, las entradas `NaN` y `±Inf` en `A` se trataban de manera inconsistente.


# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rmul!(A, 2)
2×2 Matrix{Int64}:
 2  4
 6  8

julia> rmul!([NaN], 0.0)
1-element Vector{Float64}:
 NaN
```
