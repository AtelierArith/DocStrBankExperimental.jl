```
eigvecs(A, B) -> Matrix
```

Devuelve una matriz `M` cuyas columnas son los eigenvectores generalizados de `A` y `B`. (El `k`-ésimo eigenvector se puede obtener del corte `M[:, k]`.)

# Ejemplos

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
