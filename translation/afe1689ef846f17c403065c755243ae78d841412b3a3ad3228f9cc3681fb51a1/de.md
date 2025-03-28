```
dayofweekofmonth(dt::TimeType) -> Int
```

Für den Wochentag von `dt` gibt es die Nummer, die er im Monat von `dt` hat. Wenn der Wochentag von `dt` Montag ist, dann ist `1 = Erster Montag des Monats, 2 = Zweiter Montag des Monats, usw.` Im Bereich 1:5.

# Beispiele

```jldoctest
julia> dayofweekofmonth(Date("2000-02-01"))
1

julia> dayofweekofmonth(Date("2000-02-08"))
2

julia> dayofweekofmonth(Date("2000-02-15"))
3
```
