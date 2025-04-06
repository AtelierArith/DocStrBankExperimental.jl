```
eigvecs(A, B) -> Matrix
```

Gibt eine Matrix `M` zurück, deren Spalten die verallgemeinerten Eigenvektoren von `A` und `B` sind. (Der `k`te Eigenvektor kann aus dem Slice `M[:, k]` abgerufen werden.)

# Beispiele

```jldoctest
julia> A = [1 0; 0 -1]
2×2 Matrix{Int64}:
 1   0
 0  -1

julia> B = [0 1; 1 0]
2×2 Matrix{Int64}:
 0  1
 1  0

julia> eigvecs(A, B)
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im
```
