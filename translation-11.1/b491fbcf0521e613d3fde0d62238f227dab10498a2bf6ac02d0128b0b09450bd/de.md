```
logdet(M)
```

Logarithmus der Determinante einer Matrix. Entspricht `log(det(M))`, kann jedoch eine höhere Genauigkeit bieten und Überlauf/Unterlauf vermeiden.

# Beispiele

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
