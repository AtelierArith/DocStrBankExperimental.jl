```
chomp(s::AbstractString) -> SubString
```

Elimina un solo salto de línea al final de una cadena.

Ver también [`chop`](@ref).

# Ejemplos

```jldoctest
julia> chomp("Hello\n")
"Hello"
```
