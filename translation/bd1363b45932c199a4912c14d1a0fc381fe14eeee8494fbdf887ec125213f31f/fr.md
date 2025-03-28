```
isletter(c::AbstractChar) -> Bool
```

Testez si un caractère est une lettre. Un caractère est classé comme une lettre s'il appartient à la catégorie générale Unicode Lettre, c'est-à-dire un caractère dont le code de catégorie commence par 'L'.

Voir aussi : [`isdigit`](@ref).

# Exemples

```jldoctest
julia> isletter('❤')
false

julia> isletter('α')
true

julia> isletter('9')
false
```
