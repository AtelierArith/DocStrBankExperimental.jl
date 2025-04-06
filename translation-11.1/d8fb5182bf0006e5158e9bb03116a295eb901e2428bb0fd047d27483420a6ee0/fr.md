```
isuppercase(c::AbstractChar) -> Bool
```

Teste si un caractère est une lettre majuscule (selon la propriété dérivée `Uppercase` de la norme Unicode).

Voir aussi [`islowercase`](@ref).

# Exemples

```jldoctest
julia> isuppercase('γ')
false

julia> isuppercase('Γ')
true

julia> isuppercase('❤')
false
```
