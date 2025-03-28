```
now(::Type{UTC}) -> DateTime
```

Devuelve un `DateTime` correspondiente a la hora del sistema del usuario en UTC/GMT. Para otras zonas horarias, consulta el paquete TimeZones.jl.

# Ejemplos

```julia
julia> now(UTC)
2023-01-04T10:52:24.864
```
