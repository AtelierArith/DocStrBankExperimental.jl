```
now(::Type{UTC}) -> DateTime
```

Renvoie un `DateTime` correspondant à l'heure système de l'utilisateur en UTC/GMT. Pour d'autres fuseaux horaires, voir le package TimeZones.jl.

# Exemples

```julia
julia> now(UTC)
2023-01-04T10:52:24.864
```
