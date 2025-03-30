```
startswith(s::AbstractString, prefix::Union{AbstractString,Base.Chars})
```

`prefix` ile başlayan `s` için `true` döner; `prefix` bir dize, bir karakter veya karakterlerin bir demeti/vektörü/kümesi olabilir. Eğer `prefix` bir demet/vektör/küme ise, `s`'nin ilk karakterinin o kümenin bir parçası olup olmadığını test edin.

Ayrıca [`endswith`](@ref), [`contains`](@ref) bakınız.

# Örnekler

```jldoctest
julia> startswith("JuliaLang", "Julia")
true
```
