```
islowercase(c::AbstractChar) -> Bool
```

Teste si un caractère est une lettre minuscule (selon la propriété dérivée `Lowercase` de la norme Unicode).

Voir aussi [`isuppercase`](@ref).

# Exemples

```jldoctest
julia> islowercase('α')
true

julia> islowercase('Γ')
false

julia> islowercase('❤')
false
```
