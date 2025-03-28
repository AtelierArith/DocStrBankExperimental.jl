```
RoundingMode
```

Un tipo utilizado para controlar el modo de redondeo de las operaciones de punto flotante (a través de las funciones [`rounding`](@ref)/[`setrounding`](@ref)), o como argumentos opcionales para redondear al entero más cercano (a través de la función [`round`](@ref)).

Los modos de redondeo actualmente soportados son:

  * [`RoundNearest`](@ref) (predeterminado)
  * [`RoundNearestTiesAway`](@ref)
  * [`RoundNearestTiesUp`](@ref)
  * [`RoundToZero`](@ref)
  * [`RoundFromZero`](@ref)
  * [`RoundUp`](@ref)
  * [`RoundDown`](@ref)

!!! compat "Julia 1.9"
    `RoundFromZero` requiere al menos Julia 1.9. Las versiones anteriores solo soportan `RoundFromZero` para `BigFloat`s.

