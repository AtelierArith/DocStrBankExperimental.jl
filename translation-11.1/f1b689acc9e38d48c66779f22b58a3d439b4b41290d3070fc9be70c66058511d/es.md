```
chopprefix(s::AbstractString, prefix::Union{AbstractString,Regex}) -> SubString
```

Elimina el prefijo `prefix` de `s`. Si `s` no comienza con `prefix`, se devuelve una cadena igual a `s`.

Véase también [`chopsuffix`](@ref).

!!! compat "Julia 1.8"
    Esta función está disponible a partir de Julia 1.8.


# Ejemplos

```jldoctest
julia> chopprefix("Hamburger", "Ham")
"burger"

julia> chopprefix("Hamburger", "hotdog")
"Hamburger"
```
