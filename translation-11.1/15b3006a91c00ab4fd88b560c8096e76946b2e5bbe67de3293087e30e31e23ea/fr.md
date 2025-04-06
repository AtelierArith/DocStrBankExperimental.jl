```
eigen(A::Union{SymTridiagonal, Hermitian, Symmetric}, vl::Real, vu::Real) -> Eigen
```

Calcule la décomposition en valeurs propres de `A`, retournant un objet de factorisation [`Eigen`](@ref) `F` qui contient les valeurs propres dans `F.values` et les vecteurs propres dans les colonnes de la matrice `F.vectors`. (Le `k`-ième vecteur propre peut être obtenu à partir de la tranche `F.vectors[:, k]`.)

L'itération de la décomposition produit les composants `F.values` et `F.vectors`.

Les fonctions suivantes sont disponibles pour les objets `Eigen` : [`inv`](@ref), [`det`](@ref), et [`isposdef`](@ref).

`vl` est la borne inférieure de la fenêtre des valeurs propres à rechercher, et `vu` est la borne supérieure.

!!! note
    Si [`vl`, `vu`] ne contient pas toutes les valeurs propres de `A`, alors la factorisation retournée sera une factorisation *tronquée*.

