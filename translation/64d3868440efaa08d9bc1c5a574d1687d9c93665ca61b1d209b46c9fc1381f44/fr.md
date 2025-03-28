```
isleapyear(dt::TimeType) -> Bool
```

Retourne `true` si l'année de `dt` est une année bissextile.

# Exemples

```jldoctest
julia> isleapyear(Date("2004"))
true

julia> isleapyear(Date("2005"))
false
```
