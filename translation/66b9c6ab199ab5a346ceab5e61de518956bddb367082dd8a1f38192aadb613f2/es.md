```
eigvals(A; permute::Bool=true, scale::Bool=true, sortby) -> values
```

Devuelve los valores propios de `A`.

Para matrices generales no simétricas, es posible especificar cómo se balancea la matriz antes del cálculo de los valores propios. Las palabras clave `permute`, `scale` y `sortby` son las mismas que para [`eigen`](@ref).

# Ejemplos

```jldoctest
julia> diag_matrix = [1 0; 0 4]
2×2 Matrix{Int64}:
 1  0
 0  4

julia> eigvals(diag_matrix)
2-element Vector{Float64}:
 1.0
 4.0
```
