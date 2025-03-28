```
Float32(x [, mode::RoundingMode])
```

Crea un `Float32` a partir de `x`. Si `x` no es representable exactamente, entonces `mode` determina cómo se redondea `x`.

# Ejemplos

```jldoctest
julia> Float32(1/3, RoundDown)
0.3333333f0

julia> Float32(1/3, RoundUp)
0.33333334f0
```

Consulta [`RoundingMode`](@ref) para los modos de redondeo disponibles. ```
