```
now(::Type{UTC}) -> DateTime
```

Kullanıcının sistem saatine karşılık gelen bir `DateTime` döndürür, UTC/GMT olarak. Diğer saat dilimleri için TimeZones.jl paketine bakın.

# Örnekler

```julia
julia> now(UTC)
2023-01-04T10:52:24.864
```
