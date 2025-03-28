```
isdigit(c::AbstractChar) -> Bool
```

Teste si un caractère est un chiffre décimal (0-9).

Voir aussi : [`isletter`](@ref).

# Exemples

```jldoctest
julia> isdigit('❤')
false

julia> isdigit('9')
true

julia> isdigit('α')
false
```
