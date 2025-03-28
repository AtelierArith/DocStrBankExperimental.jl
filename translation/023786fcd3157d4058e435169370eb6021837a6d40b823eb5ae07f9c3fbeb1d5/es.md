```
^(b::Número, A::MatrizAbstracta)
```

Exponencial de matriz, equivalente a $\exp(\log(b)A)$.

!!! compat "Julia 1.1"
    Se agregó soporte para elevar números `Irrational` (como `ℯ`) a una matriz en Julia 1.1.


# Ejemplos

```jldoctest
julia> 2^[1 2; 0 3]
2×2 Matriz{Float64}:
 2.0  6.0
 0.0  8.0

julia> ℯ^[1 2; 0 3]
2×2 Matriz{Float64}:
 2.71828  17.3673
 0.0      20.0855
```
