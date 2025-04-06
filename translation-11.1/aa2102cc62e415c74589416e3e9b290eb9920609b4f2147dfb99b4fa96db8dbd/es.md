```
findlast(pattern::AbstractString, string::AbstractString)
```

Encuentra la última ocurrencia de `pattern` en `string`. Equivalente a [`findprev(pattern, string, lastindex(string))`](@ref).

# Ejemplos

```jldoctest
julia> findlast("o", "Hello to the world")
15:15

julia> findfirst("Julia", "JuliaLang")
1:5
```
