```
findmax(A; dims) -> (maxval, index)
```

Para una entrada de matriz, devuelve el valor y el índice del máximo sobre las dimensiones dadas. `NaN` se trata como mayor que todos los demás valores excepto `missing`.

# Ejemplos

```jldoctest
julia> A = [1.0 2; 3 4]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> findmax(A, dims=1)
([3.0 4.0], CartesianIndex{2}[CartesianIndex(2, 1) CartesianIndex(2, 2)])

julia> findmax(A, dims=2)
([2.0; 4.0;;], CartesianIndex{2}[CartesianIndex(1, 2); CartesianIndex(2, 2);;])
```
