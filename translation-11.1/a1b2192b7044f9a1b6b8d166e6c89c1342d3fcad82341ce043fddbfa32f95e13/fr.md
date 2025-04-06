```
isposdef(A) -> Bool
```

Testez si une matrice est définie positive (et Hermitienne) en essayant d'effectuer une factorisation de Cholesky de `A`.

Voir aussi [`isposdef!`](@ref), [`cholesky`](@ref).

# Exemples

```jldoctest
julia> A = [1 2; 2 50]
2×2 Matrix{Int64}:
 1   2
 2  50

julia> isposdef(A)
true
```
