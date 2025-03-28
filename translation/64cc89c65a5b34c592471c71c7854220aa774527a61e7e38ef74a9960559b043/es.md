```
prod(A::AbstractArray; dims)
```

Multiplica los elementos de un array a lo largo de las dimensiones dadas.

# Ejemplos

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> prod(A, dims=1)
1×2 Matrix{Int64}:
 3  8

julia> prod(A, dims=2)
2×1 Matrix{Int64}:
  2
 12
```
