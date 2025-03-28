```
rot180(A, k)
```

Rote la matriz `A` 180 grados un número entero `k` de veces. Si `k` es par, esto es equivalente a una `copia`.

# Ejemplos

```jldoctest
julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> rot180(a,1)
2×2 Matrix{Int64}:
 4  3
 2  1

julia> rot180(a,2)
2×2 Matrix{Int64}:
 1  2
 3  4
```
