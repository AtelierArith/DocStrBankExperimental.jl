```
clamp(x, lo, hi)
```

Devuelve `x` si `lo <= x <= hi`. Si `x > hi`, devuelve `hi`. Si `x < lo`, devuelve `lo`. Los argumentos se promueven a un tipo común.

Véase también [`clamp!`](@ref), [`min`](@ref), [`max`](@ref).

!!! compat "Julia 1.3"
    `missing` como el primer argumento requiere al menos Julia 1.3.


# Ejemplos

```jldoctest
julia> clamp.([pi, 1.0, big(10)], 2.0, 9.0)
3-element Vector{BigFloat}:
 3.141592653589793238462643383279502884197169399375105820974944592307816406286198
 2.0
 9.0

julia> clamp.([11, 8, 5], 10, 6)  # un ejemplo donde lo > hi
3-element Vector{Int64}:
  6
  6
 10
```
