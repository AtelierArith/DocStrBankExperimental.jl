```
Bidiagonal(dv::V, ev::V, uplo::Symbol) where V <: AbstractVector
```

Construit une matrice bidiagonale supérieure (`uplo=:U`) ou inférieure (`uplo=:L`) en utilisant les vecteurs diagonaux (`dv`) et hors-diagonaux (`ev`) donnés. Le résultat est de type `Bidiagonal` et fournit des solveurs linéaires spécialisés efficaces, mais peut être converti en une matrice régulière avec [`convert(Array, _)`](@ref) (ou `Array(_)` pour faire court). La longueur de `ev` doit être inférieure d'un à la longueur de `dv`.

# Exemples

```jldoctest
julia> dv = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> ev = [7, 8, 9]
3-element Vector{Int64}:
 7
 8
 9

julia> Bu = Bidiagonal(dv, ev, :U) # ev est sur la première superdiagonale
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  7  ⋅  ⋅
 ⋅  2  8  ⋅
 ⋅  ⋅  3  9
 ⋅  ⋅  ⋅  4

julia> Bl = Bidiagonal(dv, ev, :L) # ev est sur la première sous-diagonale
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅
 7  2  ⋅  ⋅
 ⋅  8  3  ⋅
 ⋅  ⋅  9  4
```
