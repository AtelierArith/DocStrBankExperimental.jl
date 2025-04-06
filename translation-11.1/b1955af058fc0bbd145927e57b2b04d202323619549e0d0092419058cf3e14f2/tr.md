```
endswith(s::AbstractString, suffix::Union{AbstractString,Base.Chars})
```

`suffix` ile bitip bitmediğini kontrol etmek için `s`'yi `true` döndürür; `suffix` bir dize, bir karakter veya bir karakterler demeti/vektörü/kümesi olabilir. Eğer `suffix` bir demet/vektör/küme ise, `s`'nin son karakterinin bu kümenin bir parçası olup olmadığını test edin.

Ayrıca [`startswith`](@ref), [`contains`](@ref) bakınız.

# Örnekler

```jldoctest
julia> endswith("Sunday", "day")
true
```
