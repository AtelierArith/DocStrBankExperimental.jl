```
eigvals!(A::Union{SymTridiagonal, Hermitian, Symmetric}, irange::UnitRange) -> values
```

Identique à [`eigvals`](@ref), mais économise de l'espace en écrasant l'entrée `A`, au lieu de créer une copie. `irange` est une plage d'*indices* de valeurs propres à rechercher - par exemple, les 2ème à 8ème valeurs propres.
