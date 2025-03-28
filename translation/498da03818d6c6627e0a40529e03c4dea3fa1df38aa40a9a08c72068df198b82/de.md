```
daysinmonth(dt::TimeType) -> Int
```

Gibt die Anzahl der Tage im Monat von `dt` zurück. Der Wert kann 28, 29, 30 oder 31 sein.

# Beispiele

```jldoctest
julia> daysinmonth(Date("2000-01"))
31

julia> daysinmonth(Date("2001-02"))
28

julia> daysinmonth(Date("2000-02"))
29
```
