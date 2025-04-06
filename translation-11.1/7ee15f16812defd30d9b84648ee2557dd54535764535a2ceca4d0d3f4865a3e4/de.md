```
clamp(x, lo, hi)
```

Gibt `x` zurück, wenn `lo <= x <= hi`. Wenn `x > hi`, wird `hi` zurückgegeben. Wenn `x < lo`, wird `lo` zurückgegeben. Die Argumente werden auf einen gemeinsamen Typ befördert.

Siehe auch [`clamp!`](@ref), [`min`](@ref), [`max`](@ref).

!!! compat "Julia 1.3"
    `missing` als erstes Argument erfordert mindestens Julia 1.3.


# Beispiele

```jldoctest
julia> clamp.([pi, 1.0, big(10)], 2.0, 9.0)
3-element Vector{BigFloat}:
 3.141592653589793238462643383279502884197169399375105820974944592307816406286198
 2.0
 9.0

julia> clamp.([11, 8, 5], 10, 6)  # ein Beispiel, bei dem lo > hi
3-element Vector{Int64}:
  6
  6
 10
```
