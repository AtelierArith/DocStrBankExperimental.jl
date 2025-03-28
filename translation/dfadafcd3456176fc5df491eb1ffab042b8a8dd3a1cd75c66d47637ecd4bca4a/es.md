```
argmin(A; dims) -> indices
```

Para una entrada de matriz, devuelve los índices de los elementos mínimos sobre las dimensiones dadas. `NaN` se trata como menor que todos los demás valores excepto `missing`.

# Ejemplos

```jldoctest
julia> A = [1.0 2; 3 4]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> argmin(A, dims=1)
1×2 Matrix{CartesianIndex{2}}:
 CartesianIndex(1, 1)  CartesianIndex(1, 2)

julia> argmin(A, dims=2)
2×1 Matrix{CartesianIndex{2}}:
 CartesianIndex(1, 1)
 CartesianIndex(2, 1)
```
