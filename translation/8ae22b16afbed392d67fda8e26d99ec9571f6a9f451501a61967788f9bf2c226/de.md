```
daysofweekinmonth(dt::TimeType) -> Int
```

Für den Wochentag von `dt` gibt die Funktion die Gesamtzahl dieses Wochentags im Monat von `dt` zurück. Gibt 4 oder 5 zurück. Nützlich in zeitlichen Ausdrücken, um den letzten Tag einer Woche in einem Monat anzugeben, indem `dayofweekofmonth(dt) == daysofweekinmonth(dt)` in der Anpassungsfunktion enthalten ist.

# Beispiele

```jldoctest
julia> daysofweekinmonth(Date("2005-01-01"))
5

julia> daysofweekinmonth(Date("2005-01-04"))
4
```
