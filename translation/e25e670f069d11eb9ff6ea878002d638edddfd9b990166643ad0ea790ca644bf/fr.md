```
isxdigit(c::AbstractChar) -> Bool
```

Testez si un caractère est un chiffre hexadécimal valide. Notez que cela n'inclut pas `x` (comme dans le préfixe standard `0x`).

# Exemples

```jldoctest
julia> isxdigit('a')
true

julia> isxdigit('x')
false
```
