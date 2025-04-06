```
contains(haystack::AbstractString, needle)
```

Retourne `true` si `haystack` contient `needle`. C'est la même chose que `occursin(needle, haystack)`, mais est fourni pour la cohérence avec `startswith(haystack, needle)` et `endswith(haystack, needle)`.

Voir aussi [`occursin`](@ref), [`in`](@ref), [`issubset`](@ref).

# Exemples

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
    La fonction `contains` nécessite au moins Julia 1.5.

