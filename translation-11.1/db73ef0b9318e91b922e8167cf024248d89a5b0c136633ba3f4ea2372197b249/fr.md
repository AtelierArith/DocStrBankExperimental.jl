```
eigen(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> Eigen
```

Calcule la décomposition en valeurs propres de `A`, retournant un objet de factorisation [`Eigen`](@ref) `F` qui contient les valeurs propres dans `F.values` et les vecteurs propres dans les colonnes de la matrice `F.vectors`. (Le `k`-ème vecteur propre peut être obtenu à partir de la tranche `F.vectors[:, k]`.)

L'itération de la décomposition produit les composants `F.values` et `F.vectors`.

Les fonctions suivantes sont disponibles pour les objets `Eigen` : [`inv`](@ref), [`det`](@ref), et [`isposdef`](@ref).

La [`UnitRange`](@ref) `irange` spécifie les indices des valeurs propres triées à rechercher.

!!! note
    Si `irange` n'est pas `1:n`, où `n` est la dimension de `A`, alors la factorisation retournée sera une factorisation *tronquée*.

