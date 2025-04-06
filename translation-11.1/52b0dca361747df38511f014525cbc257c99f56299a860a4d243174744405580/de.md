```
^(A::AbstractMatrix, p::Number)
```

Matrix-Potenz, äquivalent zu $\exp(p\log(A))$

# Beispiele

```jldoctest
julia> [1 2; 0 3]^3
2×2 Matrix{Int64}:
 1  26
 0  27
```
