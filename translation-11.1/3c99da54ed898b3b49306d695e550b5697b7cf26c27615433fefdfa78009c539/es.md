```
inv(M)
```

Inversa de matriz. Calcula la matriz `N` tal que `M * N = I`, donde `I` es la matriz identidad. Se calcula resolviendo la división izquierda `N = M \ I`.

# Ejemplos

```jldoctest
julia> M = [2 5; 1 3]
2×2 Matrix{Int64}:
 2  5
 1  3

julia> N = inv(M)
2×2 Matrix{Float64}:
  3.0  -5.0
 -1.0   2.0

julia> M*N == N*M == Matrix(I, 2, 2)
true
```
