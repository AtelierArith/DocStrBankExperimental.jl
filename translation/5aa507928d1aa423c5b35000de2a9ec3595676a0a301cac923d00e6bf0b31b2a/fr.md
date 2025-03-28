```
median(A::AbstractArray; dims)
```

Calcule la médiane d'un tableau le long des dimensions données.

# Exemples

```jldoctest
julia> using Statistics

julia> median([1 2; 3 4], dims=1)
1×2 Matrix{Float64}:
 2.0  3.0
```
