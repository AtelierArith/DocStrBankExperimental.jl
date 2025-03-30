```
contains(haystack::AbstractString, needle)
```

`haystack` içinde `needle` varsa `true` döner. Bu, `occursin(needle, haystack)` ile aynıdır, ancak `startswith(haystack, needle)` ve `endswith(haystack, needle)` ile tutarlılık sağlamak için sunulmuştur.

Ayrıca bkz. [`occursin`](@ref), [`in`](@ref), [`issubset`](@ref).

# Örnekler

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
    `contains` fonksiyonu en az Julia 1.5 gerektirir.

