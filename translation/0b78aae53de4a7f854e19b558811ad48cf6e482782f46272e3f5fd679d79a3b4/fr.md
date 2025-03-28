```
Float32(x [, mode::RoundingMode])
```

Crée un `Float32` à partir de `x`. Si `x` n'est pas exactement représentable, alors `mode` détermine comment `x` est arrondi.

# Exemples

```jldoctest
julia> Float32(1/3, RoundDown)
0.3333333f0

julia> Float32(1/3, RoundUp)
0.33333334f0
```

Voir [`RoundingMode`](@ref) pour les modes d'arrondi disponibles. ```
