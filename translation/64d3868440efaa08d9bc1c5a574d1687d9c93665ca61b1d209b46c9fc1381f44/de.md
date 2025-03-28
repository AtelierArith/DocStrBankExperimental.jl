```
isleapyear(dt::TimeType) -> Bool
```

Gibt `true` zurück, wenn das Jahr von `dt` ein Schaltjahr ist.

# Beispiele

```jldoctest
julia> isleapyear(Date("2004"))
true

julia> isleapyear(Date("2005"))
false
```
