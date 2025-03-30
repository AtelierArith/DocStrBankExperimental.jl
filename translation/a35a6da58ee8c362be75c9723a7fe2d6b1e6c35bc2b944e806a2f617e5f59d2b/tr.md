```
monthabbr(dt::TimeType; locale="türkçe") -> String
monthabbr(month::Integer, locale="türkçe") -> String
```

Verilen `locale`'deki `Date` veya `DateTime` veya `Integer`'ın kısaltılmış ay adını döndürür.

# Örnekler

```jldoctest
julia> monthabbr(Date("2005-01-04"))
"Jan"

julia> monthabbr(2)
"Feb"
```
