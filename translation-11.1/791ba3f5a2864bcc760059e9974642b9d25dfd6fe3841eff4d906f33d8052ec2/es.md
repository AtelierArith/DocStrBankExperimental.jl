```
findfirst(pattern::AbstractString, string::AbstractString)
findfirst(pattern::AbstractPattern, string::String)
```

Encuentra la primera ocurrencia de `pattern` en `string`. Equivalente a [`findnext(pattern, string, firstindex(s))`](@ref).

# Ejemplos

```jldoctest
julia> findfirst("z", "Hello to the world") # no devuelve nada, pero no se imprime en el REPL

julia> findfirst("Julia", "JuliaLang")
1:5
```
