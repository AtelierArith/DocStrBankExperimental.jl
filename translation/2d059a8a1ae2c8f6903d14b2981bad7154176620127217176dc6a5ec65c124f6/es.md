```
startswith(s::AbstractString, prefix::Union{AbstractString,Base.Chars})
```

Devuelve `true` si `s` comienza con `prefix`, que puede ser una cadena, un carácter o una tupla/vector/conjunto de caracteres. Si `prefix` es una tupla/vector/conjunto de caracteres, prueba si el primer carácter de `s` pertenece a ese conjunto.

Véase también [`endswith`](@ref), [`contains`](@ref).

# Ejemplos

```jldoctest
julia> startswith("JuliaLang", "Julia")
true
```
