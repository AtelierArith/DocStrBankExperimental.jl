```
UpperHessenberg(A::AbstractMatrix)
```

Construit une vue `UpperHessenberg` de la matrice `A`. Les entrées de `A` en dessous de la première sous-diagonale sont ignorées.

!!! compat "Julia 1.3"
    Ce type a été ajouté dans Julia 1.3.


Des algorithmes efficaces sont implémentés pour `H \ b`, `det(H)`, et similaires.

Voir aussi la fonction [`hessenberg`](@ref) pour factoriser n'importe quelle matrice en une matrice supérieure de Hessenberg similaire.

Si `F::Hessenberg` est l'objet de factorisation, la matrice unitaire peut être accédée avec `F.Q` et la matrice de Hessenberg avec `F.H`. Lorsque `Q` est extrait, le type résultant est l'objet `HessenbergQ`, et peut être converti en une matrice régulière avec [`convert(Array, _)`](@ref) (ou `Array(_)` pour faire court).

L'itération de la décomposition produit les facteurs `F.Q` et `F.H`.

# Exemples

```jldoctest
julia> A = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
4×4 Matrix{Int64}:
  1   2   3   4
  5   6   7   8
  9  10  11  12
 13  14  15  16

julia> UpperHessenberg(A)
4×4 UpperHessenberg{Int64, Matrix{Int64}}:
 1   2   3   4
 5   6   7   8
 ⋅  10  11  12
 ⋅   ⋅  15  16
```
