```
lowercase(s::AbstractString)
```

Tüm karakterleri küçük harfe dönüştürerek `s`'yi döndürür.

Ayrıca bkz. [`uppercase`](@ref), [`titlecase`](@ref), [`lowercasefirst`](@ref).

# Örnekler

```jldoctest
julia> lowercase("STRINGS AND THINGS")
"strings and things"
```
