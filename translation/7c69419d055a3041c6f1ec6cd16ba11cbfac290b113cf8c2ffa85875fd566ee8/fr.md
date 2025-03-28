```
isposdef!(A) -> Bool
```

Testez si une matrice est définie positive (et Hermitienne) en essayant d'effectuer une factorisation de Cholesky de `A`, en écrasant `A` dans le processus. Voir aussi [`isposdef`](@ref).

# Exemples

```jldoctest
julia> A = [1. 2.; 2. 50.];

julia> isposdef!(A)
true

julia> A
2×2 Matrix{Float64}:
 1.0  2.0
 2.0  6.78233
```
