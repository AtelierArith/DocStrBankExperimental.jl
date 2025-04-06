```
iscntrl(c::AbstractChar) -> Bool
```

Teste si un caractère est un caractère de contrôle. Les caractères de contrôle sont les caractères non imprimables du sous-ensemble Latin-1 de l'Unicode.

# Exemples

```jldoctest
julia> iscntrl('\x01')
true

julia> iscntrl('a')
false
```
