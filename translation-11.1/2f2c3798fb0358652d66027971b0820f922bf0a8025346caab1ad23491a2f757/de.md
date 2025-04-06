```
maximum(A::AbstractArray; dims)
```

Berechne den maximalen Wert eines Arrays über die angegebenen Dimensionen. Siehe auch die [`max(a,b)`](@ref) Funktion, um das Maximum von zwei oder mehr Argumenten zu nehmen, die elementweise auf Arrays über `max.(a,b)` angewendet werden können.

Siehe auch: [`maximum!`](@ref), [`extrema`](@ref), [`findmax`](@ref), [`argmax`](@ref).

# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> maximum(A, dims=1)
1×2 Matrix{Int64}:
 3  4

julia> maximum(A, dims=2)
2×1 Matrix{Int64}:
 2
 4
```
