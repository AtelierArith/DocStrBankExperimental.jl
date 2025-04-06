```
week(dt::TimeType) -> Int64
```

Renvoie la [date de semaine ISO](https://en.wikipedia.org/wiki/ISO_week_date) d'un `Date` ou `DateTime` sous forme d'un [`Int64`](@ref). Notez que la première semaine de l'année est celle qui contient le premier jeudi de l'année, ce qui peut entraîner des dates antérieures au 4 janvier étant dans la dernière semaine de l'année précédente. Par exemple, `week(Date(2005, 1, 1))` est la 53e semaine de 2004.

# Exemples

```jldoctest
julia> week(Date(1989, 6, 22))
25

julia> week(Date(2005, 1, 1))
53

julia> week(Date(2004, 12, 31))
53
```
