```
now(::Type{UTC}) -> DateTime
```

Gibt ein `DateTime` zurück, das der Systemzeit des Benutzers als UTC/GMT entspricht. Für andere Zeitzonen siehe das TimeZones.jl-Paket.

# Beispiele

```julia
julia> now(UTC)
2023-01-04T10:52:24.864
```
