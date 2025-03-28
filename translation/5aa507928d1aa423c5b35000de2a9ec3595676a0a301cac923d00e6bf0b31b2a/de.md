```
median(A::AbstractArray; dims)
```

Berechne den Median eines Arrays entlang der angegebenen Dimensionen.

# Beispiele

```jldoctest
julia> using Statistics

julia> median([1 2; 3 4], dims=1)
1×2 Matrix{Float64}:
 2.0  3.0
```
