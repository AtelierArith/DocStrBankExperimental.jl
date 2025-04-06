```
logdet(M)
```

Logaritmo del determinante de la matriz. Equivalente a `log(det(M))`, pero puede proporcionar mayor precisión y evita desbordamiento/subdesbordamiento.

# Ejemplos

```jldoctest
julia> M = [1 0; 2 2]
2×2 Matrix{Int64}:
 1  0
 2  2

julia> logdet(M)
0.6931471805599453

julia> logdet(Matrix(I, 3, 3))
0.0
```
