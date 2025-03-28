```
occursin(needle::Union{AbstractString,AbstractPattern,AbstractChar}, haystack::AbstractString)
```

Bestimmen Sie, ob das erste Argument ein Teilstring des zweiten ist. Wenn `needle` ein regulärer Ausdruck ist, wird überprüft, ob `haystack` ein Treffer enthält.

# Beispiele

```jldoctest
julia> occursin("Julia", "JuliaLang ist ziemlich cool!")
true

julia> occursin('a', "JuliaLang ist ziemlich cool!")
true

julia> occursin(r"a.a", "aba")
true

julia> occursin(r"a.a", "abba")
false
```

Siehe auch [`contains`](@ref).
