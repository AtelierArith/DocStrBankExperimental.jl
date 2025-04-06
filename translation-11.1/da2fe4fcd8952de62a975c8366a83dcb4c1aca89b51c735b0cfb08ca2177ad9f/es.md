```
chopsuffix(s::AbstractString, suffix::Union{AbstractString,Regex}) -> SubString
```

Elimina el sufijo `suffix` de `s`. Si `s` no termina con `suffix`, se devuelve una cadena igual a `s`.

Véase también [`chopprefix`](@ref).

!!! compat "Julia 1.8"
    Esta función está disponible a partir de Julia 1.8.


# Ejemplos

```jldoctest
julia> chopsuffix("Hamburger", "er")
"Hamburg"

julia> chopsuffix("Hamburger", "hotdog")
"Hamburger"
```
