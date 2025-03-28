```
mean(A::AbstractArray; dims)
```

Calcula la media de un array sobre las dimensiones dadas.

!!! compat "Julia 1.1"
    `mean` para arrays vacíos requiere al menos Julia 1.1.


# Ejemplos

```jldoctest
julia> using Statistics

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> mean(A, dims=1)
1×2 Matrix{Float64}:
 2.0  3.0

julia> mean(A, dims=2)
2×1 Matrix{Float64}:
 1.5
 3.5
```
