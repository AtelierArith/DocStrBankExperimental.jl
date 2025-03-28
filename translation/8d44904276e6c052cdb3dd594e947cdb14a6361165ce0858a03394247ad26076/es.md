```
chop(s::AbstractString; head::Integer = 0, tail::Integer = 1)
```

Elimina los primeros `head` y los últimos `tail` caracteres de `s`. La llamada `chop(s)` elimina el último carácter de `s`. Si se solicita eliminar más caracteres de los que tiene `length(s)`, se devuelve una cadena vacía.

Véase también [`chomp`](@ref), [`startswith`](@ref), [`first`](@ref).

# Ejemplos

```jldoctest
julia> a = "March"
"March"

julia> chop(a)
"Marc"

julia> chop(a, head = 1, tail = 2)
"ar"

julia> chop(a, head = 5, tail = 5)
""
```
