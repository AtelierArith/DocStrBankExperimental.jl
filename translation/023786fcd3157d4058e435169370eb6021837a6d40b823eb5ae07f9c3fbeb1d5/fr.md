```
^(b::Number, A::AbstractMatrix)
```

Exponential de matrice, équivalent à $\exp(\log(b)A)$.

!!! compat "Julia 1.1"
    Le support pour l'élévation des nombres `Irrational` (comme `ℯ`) à une matrice a été ajouté dans Julia 1.1.


# Exemples

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
