```
eps(::Type{DateTime}) -> Millisekunde
eps(::Type{Date}) -> Tag
eps(::Type{Time}) -> Nanosekunde
eps(::TimeType) -> Zeitraum
```

Gibt den kleinsten unterstützten Wert der Einheit für den `TimeType` zurück.

# Beispiele

```jldoctest
julia> eps(DateTime)
1 Millisekunde

julia> eps(Date)
1 Tag

julia> eps(Time)
1 Nanosekunde
```
