```
contains(haystack::AbstractString, needle)
```

Gibt `true` zurück, wenn `haystack` `needle` enthält. Dies ist dasselbe wie `occursin(needle, haystack)`, wird jedoch zur Konsistenz mit `startswith(haystack, needle)` und `endswith(haystack, needle)` bereitgestellt.

Siehe auch [`occursin`](@ref), [`in`](@ref), [`issubset`](@ref).

# Beispiele

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
    Die Funktion `contains` erfordert mindestens Julia 1.5.

