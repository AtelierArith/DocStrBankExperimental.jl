```
dayabbr(dt::TimeType; locale="türkçe") -> String
dayabbr(day::Integer; locale="türkçe") -> String
```

Verilen `locale`'deki haftanın gününe karşılık gelen kısaltılmış ismi döndürür. Ayrıca `Integer` da kabul eder.

# Örnekler

```jldoctest
julia> dayabbr(Date("2000-01-01"))
"Cum"

julia> dayabbr(3)
"Çar"
```
