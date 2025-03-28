```
logdet(M)
```

Logarithme du déterminant de matrice. Équivalent à `log(det(M))`, mais peut offrir une précision accrue et évite le débordement/sous-dépassement.

# Exemples

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
