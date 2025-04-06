```
lu(A, pivot = RowMaximum(); check = true, allowsingular = false) -> F::LU
```

Calculez la factorisation LU de `A`.

Lorsque `check = true`, une erreur est levée si la décomposition échoue. Lorsque `check = false`, la responsabilité de vérifier la validité de la décomposition (via [`issuccess`](@ref)) incombe à l'utilisateur.

Par défaut, avec `check = true`, une erreur est également levée lorsque la décomposition produit des facteurs valides, mais que le facteur triangulaire supérieur `U` est de rang déficient. Cela peut être modifié en passant `allowsingular = true`.

Dans la plupart des cas, si `A` est un sous-type `S` de `AbstractMatrix{T}` avec un type d'élément `T` supportant `+`, `-`, `*` et `/`, le type de retour est `LU{T,S{T}}`.

En général, la factorisation LU implique une permutation des lignes de la matrice (correspondant à la sortie `F.p` décrite ci-dessous), connue sous le nom de "pivotement" (car elle correspond à choisir quelle ligne contient le "pivot", l'entrée diagonale de `F.U`). L'une des stratégies de pivotement suivantes peut être sélectionnée via l'argument optionnel `pivot` :

  * `RowMaximum()` (par défaut) : la stratégie de pivotement standard ; le pivot correspond à l'élément de valeur absolue maximale parmi les lignes restantes à factoriser. Cette stratégie de pivotement nécessite que le type d'élément supporte également [`abs`](@ref) et [`<`](@ref). (C'est généralement la seule option numériquement stable pour les matrices à virgule flottante.)
  * `RowNonZero()` : le pivot correspond au premier élément non nul parmi les lignes restantes à factoriser. (Cela correspond au choix typique dans les calculs manuels, et est également utile pour des types de nombres algébriques plus généraux qui supportent [`iszero`](@ref) mais pas `abs` ou `<`.)
  * `NoPivot()` : pivotement désactivé (échouera si une entrée nulle est rencontrée dans une position de pivot, même lorsque `allowsingular = true`).

Les composants individuels de la factorisation `F` peuvent être accessibles via [`getproperty`](@ref) :

| Composant | Description                                  |
|:--------- |:-------------------------------------------- |
| `F.L`     | `L` (partie triangulaire inférieure) de `LU` |
| `F.U`     | `U` (partie triangulaire supérieure) de `LU` |
| `F.p`     | permutation `Vector` (droite)                |
| `F.P`     | permutation `Matrix` (droite)                |

L'itération de la factorisation produit les composants `F.L`, `F.U` et `F.p`.

La relation entre `F` et `A` est

`F.L*F.U == A[F.p, :]`

`F` prend également en charge les fonctions suivantes :

| Fonction prise en charge | `LU` | `LU{T,Tridiagonal{T}}` |
|:------------------------ |:---- |:---------------------- |
| [`/`](@ref)              | ✓    |                        |
| [`\`](@ref)              | ✓    | ✓                      |
| [`inv`](@ref)            | ✓    | ✓                      |
| [`det`](@ref)            | ✓    | ✓                      |
| [`logdet`](@ref)         | ✓    | ✓                      |
| [`logabsdet`](@ref)      | ✓    | ✓                      |
| [`size`](@ref)           | ✓    | ✓                      |

!!! compat "Julia 1.11"
    L'argument clé `allowsingular` a été ajouté dans Julia 1.11.


# Exemples

```jldoctest
julia> A = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> F = lu(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
Facteur L :
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
Facteur U :
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = lu(A); # déstructuration via itération

julia> l == F.L && u == F.U && p == F.p
true

julia> lu([1 2; 1 2], allowsingular = true)
LU{Float64, Matrix{Float64}, Vector{Int64}}
Facteur L :
2×2 Matrix{Float64}:
 1.0  0.0
 1.0  1.0
Facteur U (déficient en rang) :
2×2 Matrix{Float64}:
 1.0  2.0
 0.0  0.0
```
