```
^(A::AbstractMatrix, p::Number)
```

Potencia de matriz, equivalente a $\exp(p\log(A))$

# Ejemplos

```jldoctest
julia> [1 2; 0 3]^3
2×2 Matrix{Int64}:
 1  26
 0  27
```
