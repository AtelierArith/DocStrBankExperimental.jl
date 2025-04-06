```
chopprefix(s::AbstractString, prefix::Union{AbstractString,Regex}) -> SubString
```

Supprime le préfixe `prefix` de `s`. Si `s` ne commence pas par `prefix`, une chaîne égale à `s` est renvoyée.

Voir aussi [`chopsuffix`](@ref).

!!! compat "Julia 1.8"
    Cette fonction est disponible depuis Julia 1.8.


# Exemples

```jldoctest
julia> chopprefix("Hamburger", "Ham")
"burger"

julia> chopprefix("Hamburger", "hotdog")
"Hamburger"
```
