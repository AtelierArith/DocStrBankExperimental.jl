```
SymTridiagonal(dv::V, ev::V) où V <: AbstractVector
```

Construit une matrice tridiagonale symétrique à partir de la diagonale (`dv`) et de la première sous/super-diagonale (`ev`), respectivement. Le résultat est de type `SymTridiagonal` et fournit des solveurs propres spécialisés efficaces, mais peut être converti en une matrice régulière avec [`convert(Array, _)`](@ref) (ou `Array(_)` pour faire court).

Pour les matrices de blocs `SymTridiagonal`, les éléments de `dv` sont symétrisés. L'argument `ev` est interprété comme la superdiagonale. Les blocs de la sous-diagonale sont (matérialisés) transposés des blocs de la superdiagonale correspondante.

# Exemples

```jldoctest
julia> dv = [1, 2, 3, 4]
4-élément Vector{Int64}:
 1
 2
 3
 4

julia> ev = [7, 8, 9]
3-élément Vector{Int64}:
 7
 8
 9

julia> SymTridiagonal(dv, ev)
4×4 SymTridiagonal{Int64, Vector{Int64}}:
 1  7  ⋅  ⋅
 7  2  8  ⋅
 ⋅  8  3  9
 ⋅  ⋅  9  4

julia> A = SymTridiagonal(fill([1 2; 3 4], 3), fill([1 2; 3 4], 2));

julia> A[1,1]
2×2 Symmetric{Int64, Matrix{Int64}}:
 1  2
 2  4

julia> A[1,2]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> A[2,1]
2×2 Matrix{Int64}:
 1  3
 2  4
```
