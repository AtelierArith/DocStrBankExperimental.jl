```
mean(A::AbstractArray; dims)
```

Calcule la moyenne d'un tableau sur les dimensions données.

!!! compat "Julia 1.1"
    `mean` pour les tableaux vides nécessite au moins Julia 1.1.


# Exemples

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
