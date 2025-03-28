```
Unicode.isassigned(c) -> Bool
```

Gibt `true` zurück, wenn der angegebene Charakter oder die angegebene Ganzzahl ein zugewiesener Unicode-Codepunkt ist.

# Beispiele

```jldoctest
julia> Unicode.isassigned(101)
true

julia> Unicode.isassigned('\x01')
true
```
