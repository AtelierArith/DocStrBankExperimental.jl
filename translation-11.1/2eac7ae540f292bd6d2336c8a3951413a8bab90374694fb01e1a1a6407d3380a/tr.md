```
occursin(needle::Union{AbstractString,AbstractPattern,AbstractChar}, haystack::AbstractString)
```

İlk argümanın ikinci argümanın bir alt dize olup olmadığını belirler. Eğer `needle` bir düzenli ifade ise, `haystack`'in bir eşleşme içerip içermediğini kontrol eder.

# Örnekler

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

Ayrıca [`contains`](@ref) bakınız.
