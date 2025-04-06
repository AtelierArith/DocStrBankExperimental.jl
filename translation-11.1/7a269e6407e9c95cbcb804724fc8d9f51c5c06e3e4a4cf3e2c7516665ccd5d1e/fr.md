```
eigvals!(A::Union{SymTridiagonal, Hermitian, Symmetric}, vl::Real, vu::Real) -> values
```

Identique à [`eigvals`](@ref), mais économise de l'espace en écrasant l'entrée `A`, au lieu de créer une copie. `vl` est la borne inférieure de l'intervalle à rechercher pour les valeurs propres, et `vu` est la borne supérieure.
