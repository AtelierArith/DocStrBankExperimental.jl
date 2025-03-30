```
==(a::AbstractString, b::AbstractString) -> Bool
```

İki dizenin karakter karakter (teknik olarak, Unicode kod noktası bazında) eşit olup olmadığını test eder. Eğer dizelerden biri bir [`AnnotatedString`](@ref) ise, dize özelliklerinin de eşleşmesi gerekir.

# Örnekler

```jldoctest
julia> "abc" == "abc"
true

julia> "abc" == "αβγ"
false
```
