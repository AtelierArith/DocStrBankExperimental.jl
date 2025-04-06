```
^(A::AbstractMatrix, p::Number)
```

Matris kuvveti, $\exp(p\log(A))$ ile eşdeğerdir.

# Örnekler

```jldoctest
julia> [1 2; 0 3]^3
2×2 Matrix{Int64}:
 1  26
 0  27
```
