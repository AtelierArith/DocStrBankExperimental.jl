```
monthname(dt::TimeType; locale="türkçe") -> String
monthname(month::Integer, locale="türkçe") -> String
```

Verilen `locale`'deki `Date` veya `DateTime` veya `Integer`'ın ayının tam adını döndürür.

# Örnekler

```jldoctest
julia> monthname(Date("2005-01-04"))
"Ocak"

julia> monthname(2)
"Şubat"
```
