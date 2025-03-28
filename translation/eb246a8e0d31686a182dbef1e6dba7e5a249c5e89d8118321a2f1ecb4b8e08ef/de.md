```
minimum(A::AbstractArray; dims)
```

Berechne den Minimalwert eines Arrays über die angegebenen Dimensionen. Siehe auch die [`min(a,b)`](@ref) Funktion, um das Minimum von zwei oder mehr Argumenten zu nehmen, die elementweise auf Arrays über `min.(a,b)` angewendet werden können.

Siehe auch: [`minimum!`](@ref), [`extrema`](@ref), [`findmin`](@ref), [`argmin`](@ref).

# Beispiele

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> minimum(A, dims=1)
1×2 Matrix{Int64}:
 1  2

julia> minimum(A, dims=2)
2×1 Matrix{Int64}:
 1
 3
```
