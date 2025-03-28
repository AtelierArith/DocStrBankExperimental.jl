```
OrdinalRange{T, S} <: AbstractRange{T}
```

Supertype pour les plages ordinales avec des éléments de type `T` et des espacements de type `S`. Les étapes doivent toujours être des multiples exacts de [`oneunit`](@ref), et `T` doit être un type "discret", qui ne peut pas avoir de valeurs inférieures à `oneunit`. Par exemple, les types `Integer` ou `Date` seraient qualifiés, tandis que `Float64` ne le serait pas (puisque ce type peut représenter des valeurs inférieures à `oneunit(Float64)`. [`UnitRange`](@ref), [`StepRange`](@ref), et d'autres types sont des sous-types de cela.
