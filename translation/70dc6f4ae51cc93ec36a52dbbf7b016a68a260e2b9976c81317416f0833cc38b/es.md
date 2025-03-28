```
Float64(x [, mode::RoundingMode])
```

Crea un `Float64` a partir de `x`. Si `x` no es representable exactamente, entonces `mode` determina cómo se redondea `x`.

# Ejemplos

```jldoctest
julia> Float64(pi, RoundDown)
3.141592653589793

julia> Float64(pi, RoundUp)
3.1415926535897936
```

Consulta [`RoundingMode`](@ref) para los modos de redondeo disponibles.
