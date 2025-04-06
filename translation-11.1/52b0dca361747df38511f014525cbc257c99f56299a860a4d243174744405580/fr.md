```
^(A::AbstractMatrix, p::Number)
```

Puissance de matrice, équivalente à $\exp(p\log(A))$

# Exemples

```jldoctest
julia> [1 2; 0 3]^3
2×2 Matrix{Int64}:
 1  26
 0  27
```
