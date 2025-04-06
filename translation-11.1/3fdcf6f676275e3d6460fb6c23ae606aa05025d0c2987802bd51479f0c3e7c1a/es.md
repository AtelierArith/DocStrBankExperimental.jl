```
rotl90(A, k)
```

Rotea a la izquierda la matriz `A` 90 grados en sentido antihorario un número entero `k` de veces. Si `k` es un múltiplo de cuatro (incluyendo cero), esto es equivalente a una `copia`.

# Ejemplos

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rotl90(a,1)
2×2 Matrix{Int64}:
 2  4
 1  3

julia> rotl90(a,2)
2×2 Matrix{Int64}:
 4  3
 2  1

julia> rotl90(a,3)
2×2 Matrix{Int64}:
 3  1
 4  2

julia> rotl90(a,4)
2×2 Matrix{Int64}:
 1  2
 3  4
```
