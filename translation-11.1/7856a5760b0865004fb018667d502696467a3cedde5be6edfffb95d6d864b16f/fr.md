```
RoundingMode
```

Un type utilisé pour contrôler le mode d'arrondi des opérations en virgule flottante (via les fonctions [`rounding`](@ref)/[`setrounding`](@ref)), ou comme arguments optionnels pour arrondir à l'entier le plus proche (via la fonction [`round`](@ref)).

Les modes d'arrondi actuellement pris en charge sont :

  * [`RoundNearest`](@ref) (par défaut)
  * [`RoundNearestTiesAway`](@ref)
  * [`RoundNearestTiesUp`](@ref)
  * [`RoundToZero`](@ref)
  * [`RoundFromZero`](@ref)
  * [`RoundUp`](@ref)
  * [`RoundDown`](@ref)

!!! compat "Julia 1.9"
    `RoundFromZero` nécessite au moins Julia 1.9. Les versions antérieures prennent en charge `RoundFromZero` uniquement pour les `BigFloat`s.

