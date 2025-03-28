```
endswith(s::AbstractString, suffix::Union{AbstractString,Base.Chars})
```

Devuelve `true` si `s` termina con `suffix`, que puede ser una cadena, un carácter o una tupla/vector/conjunto de caracteres. Si `suffix` es una tupla/vector/conjunto de caracteres, prueba si el último carácter de `s` pertenece a ese conjunto.

Véase también [`startswith`](@ref), [`contains`](@ref).

# Ejemplos

```jldoctest
julia> endswith("Sunday", "day")
true
```
