```
^(b::Number, A::AbstractMatrix)
```

Matris üstel, $\exp(\log(b)A)$ ile eşdeğerdir.

!!! compat "Julia 1.1"
    `Irrational` sayıları (örneğin `ℯ`) bir matrise yükseltme desteği Julia 1.1'de eklendi.


# Örnekler

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
