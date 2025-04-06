```
week(dt::TimeType) -> Int64
```

Gibt die [ISO-Wochendatum](https://de.wikipedia.org/wiki/ISO_Wochendatum) eines `Date` oder `DateTime` als [`Int64`](@ref) zurück. Beachten Sie, dass die erste Woche eines Jahres die Woche ist, die den ersten Donnerstag des Jahres enthält, was dazu führen kann, dass Daten vor dem 4. Januar in der letzten Woche des vorherigen Jahres liegen. Zum Beispiel ist `week(Date(2005, 1, 1))` die 53. Woche von 2004.

# Beispiele

```jldoctest
julia> week(Date(1989, 6, 22))
25

julia> week(Date(2005, 1, 1))
53

julia> week(Date(2004, 12, 31))
53
```
