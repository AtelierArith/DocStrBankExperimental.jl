```
isprint(c::AbstractChar) -> Bool
```

Teste si un caractère est imprimable, y compris les espaces, mais pas un caractère de contrôle.

# Exemples

```jldoctest
julia> isprint('\x01')
false

julia> isprint('A')
true
```
