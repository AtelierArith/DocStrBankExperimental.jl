```
eigvecs(A; permute::Bool=true, scale::Bool=true, `sortby`) -> Matrix
```

Gibt eine Matrix `M` zurück, deren Spalten die Eigenvektoren von `A` sind. (Der `k`-te Eigenvektor kann aus dem Slice `M[:, k]` abgerufen werden.) Die Schlüsselwörter `permute`, `scale` und `sortby` sind die gleichen wie für [`eigen`](@ref).

# Beispiele

```jldoctest
julia> eigvecs([1.0 0.0 0.0; 0.0 3.0 0.0; 0.0 0.0 18.0])
3×3 Matrix{Float64}:
 1.0  0.0  0.0
 0.0  1.0  0.0
 0.0  0.0  1.0
```
