```
UnitLowerTriangular(A::AbstractMatrix)
```

Construit une vue `UnitLowerTriangular` de la matrice `A`. Une telle vue a le [`oneunit`](@ref) du [`eltype`](@ref) de `A` sur sa diagonale.

# Exemples

```jldoctest
julia> A = [1.0 2.0 3.0; 4.0 5.0 6.0; 7.0 8.0 9.0]
3×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
 7.0  8.0  9.0

julia> UnitLowerTriangular(A)
3×3 UnitLowerTriangular{Float64, Matrix{Float64}}:
 1.0   ⋅    ⋅
 4.0  1.0   ⋅
 7.0  8.0  1.0
```
