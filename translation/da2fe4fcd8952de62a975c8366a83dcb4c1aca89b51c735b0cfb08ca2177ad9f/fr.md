```
chopsuffix(s::AbstractString, suffix::Union{AbstractString,Regex}) -> SubString
```

Supprime le suffixe `suffix` de `s`. Si `s` ne se termine pas par `suffix`, une chaîne égale à `s` est renvoyée.

Voir aussi [`chopprefix`](@ref).

!!! compat "Julia 1.8"
    Cette fonction est disponible depuis Julia 1.8.


# Exemples

```jldoctest
julia> chopsuffix("Hamburger", "er")
"Hamburg"

julia> chopsuffix("Hamburger", "hotdog")
"Hamburger"
```
