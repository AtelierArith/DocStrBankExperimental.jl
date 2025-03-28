```
occursin(needle::Union{AbstractString,AbstractPattern,AbstractChar}, haystack::AbstractString)
```

Determina si el primer argumento es una subcadena del segundo. Si `needle` es una expresión regular, verifica si `haystack` contiene una coincidencia.

# Ejemplos

```jldoctest
julia> occursin("Julia", "JuliaLang is pretty cool!")
true

julia> occursin('a', "JuliaLang is pretty cool!")
true

julia> occursin(r"a.a", "aba")
true

julia> occursin(r"a.a", "abba")
false
```

Ver también [`contains`](@ref).
