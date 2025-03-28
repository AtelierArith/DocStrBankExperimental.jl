```
^(b::Number, A::AbstractMatrix)
```

Matrix-Exponential, äquivalent zu $\exp(\log(b)A)$.

!!! compat "Julia 1.1"
    Unterstützung für das Erhöhen von `Irrational` Zahlen (wie `ℯ`) auf eine Matrix wurde in Julia 1.1 hinzugefügt.


# Beispiele

```jldoctest
julia> 2^[1 2; 0 3]
2×2 Matrix{Float64}:
 2.0  6.0
 0.0  8.0

julia> ℯ^[1 2; 0 3]
2×2 Matrix{Float64}:
 2.71828  17.3673
 0.0      20.0855
```
