```
Unicode.isassigned(c) -> Bool
```

Retourne `true` si le caractère ou l'entier donné est un point de code Unicode assigné.

# Exemples

```jldoctest
julia> Unicode.isassigned(101)
true

julia> Unicode.isassigned('\x01')
true
```
