```
Tridiagonal(dl::V, d::V, du::V) où V <: AbstractVector
```

Construit une matrice tridiagonale à partir de la première sous-diagonale, de la diagonale et de la première super-diagonale, respectivement. Le résultat est de type `Tridiagonal` et fournit des solveurs linéaires spécialisés efficaces, mais peut être converti en une matrice régulière avec [`convert(Array, _)`](@ref) (ou `Array(_)` pour faire court). Les longueurs de `dl` et `du` doivent être inférieures d'une unité à la longueur de `d`.

!!! note
    La sous-diagonale `dl` et la super-diagonale `du` ne doivent pas être aliasées l'une à l'autre. Si un aliasing est détecté, le constructeur utilisera une copie de `du` comme argument.


# Exemples

```jldoctest
julia> dl = [1, 2, 3];

julia> du = [4, 5, 6];

julia> d = [7, 8, 9, 0];

julia> Tridiagonal(dl, d, du)
4×4 Tridiagonal{Int64, Vector{Int64}}:
 7  4  ⋅  ⋅
 1  8  5  ⋅
 ⋅  2  9  6
 ⋅  ⋅  3  0
```
