```
dayname(dt::TimeType; locale="türkçe") -> String
dayname(day::Integer; locale="türkçe") -> String
```

Verilen `locale`'deki haftanın gününe karşılık gelen tam gün adını döndürür. Ayrıca `Integer` da kabul eder.

# Örnekler

```jldoctest
julia> dayname(Date("2000-01-01"))
"Cumartesi"

julia> dayname(4)
"Perşembe"
```
