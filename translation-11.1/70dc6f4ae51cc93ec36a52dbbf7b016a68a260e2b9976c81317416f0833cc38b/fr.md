```
Float64(x [, mode::RoundingMode])
```

Crée un `Float64` à partir de `x`. Si `x` n'est pas exactement représentable, alors `mode` détermine comment `x` est arrondi.

# Exemples

```jldoctest
julia> Float64(pi, RoundDown)
3.141592653589793

julia> Float64(pi, RoundUp)
3.1415926535897936
```

Voir [`RoundingMode`](@ref) pour les modes d'arrondi disponibles.
