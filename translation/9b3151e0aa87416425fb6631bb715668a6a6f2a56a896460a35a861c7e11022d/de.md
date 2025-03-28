```
trunc(dt::TimeType, ::Type{Period}) -> TimeType
```

Trunkiert den Wert von `dt` gemäß dem angegebenen `Period`-Typ.

# Beispiele

```jldoctest
julia> trunc(DateTime("1996-01-01T12:30:00"), Day)
1996-01-01T00:00:00
```
