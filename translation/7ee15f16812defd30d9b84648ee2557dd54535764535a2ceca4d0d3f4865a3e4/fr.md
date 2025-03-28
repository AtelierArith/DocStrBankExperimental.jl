```
clamp(x, lo, hi)
```

Retourne `x` si `lo <= x <= hi`. Si `x > hi`, retourne `hi`. Si `x < lo`, retourne `lo`. Les arguments sont promus à un type commun.

Voir aussi [`clamp!`](@ref), [`min`](@ref), [`max`](@ref).

!!! compat "Julia 1.3"
    `missing` comme premier argument nécessite au moins Julia 1.3.


# Exemples

```jldoctest
julia> clamp.([pi, 1.0, big(10)], 2.0, 9.0)
3-element Vector{BigFloat}:
 3.141592653589793238462643383279502884197169399375105820974944592307816406286198
 2.0
 9.0

julia> clamp.([11, 8, 5], 10, 6)  # un exemple où lo > hi
3-element Vector{Int64}:
  6
  6
 10
```
