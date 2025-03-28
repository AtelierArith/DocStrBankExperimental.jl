```
isleapyear(dt::TimeType) -> Bool
```

Devuelve `true` si el año de `dt` es un año bisiesto.

# Ejemplos

```jldoctest
julia> isleapyear(Date("2004"))
true

julia> isleapyear(Date("2005"))
false
```
