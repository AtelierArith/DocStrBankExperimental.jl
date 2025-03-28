```
RoundingMode
```

Ein Typ, der verwendet wird, um den Rundungsmodus von Gleitkommaoperationen (über die Funktionen [`rounding`](@ref)/[`setrounding`](@ref)) zu steuern, oder als optionale Argumente für das Runden auf die nächste ganze Zahl (über die Funktion [`round`](@ref)).

Derzeit unterstützte Rundungsmodi sind:

  * [`RoundNearest`](@ref) (Standard)
  * [`RoundNearestTiesAway`](@ref)
  * [`RoundNearestTiesUp`](@ref)
  * [`RoundToZero`](@ref)
  * [`RoundFromZero`](@ref)
  * [`RoundUp`](@ref)
  * [`RoundDown`](@ref)

!!! compat "Julia 1.9"
    `RoundFromZero` erfordert mindestens Julia 1.9. Frühere Versionen unterstützen `RoundFromZero` nur für `BigFloat`s.

