```
contains(haystack::AbstractString, needle)
```

Devuelve `true` si `haystack` contiene `needle`. Esto es lo mismo que `occursin(needle, haystack)`, pero se proporciona para mantener la consistencia con `startswith(haystack, needle)` y `endswith(haystack, needle)`.

Véase también [`occursin`](@ref), [`in`](@ref), [`issubset`](@ref).

# Ejemplos

```jldoctest
julia> contains("JuliaLang is pretty cool!", "Julia")
true

julia> contains("JuliaLang is pretty cool!", 'a')
true

julia> contains("aba", r"a.a")
true

julia> contains("abba", r"a.a")
false
```

!!! compat "Julia 1.5"
    La función `contains` requiere al menos Julia 1.5.

