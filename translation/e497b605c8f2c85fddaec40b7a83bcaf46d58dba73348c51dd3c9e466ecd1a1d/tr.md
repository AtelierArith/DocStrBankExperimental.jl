```
uppercasefirst(s::AbstractString) -> String
```

`S`'yi ilk karakterini büyük harfe çevirerek döndürür (teknik olarak Unicode için "başlık durumu"). `S`'deki her kelimenin ilk karakterini büyük harfe çevirmek için [`titlecase`](@ref) ile de bakabilirsiniz.

Ayrıca [`lowercasefirst`](@ref), [`uppercase`](@ref), [`lowercase`](@ref), [`titlecase`](@ref) ile de bakabilirsiniz.

# Örnekler

```jldoctest
julia> uppercasefirst("python")
"Python"
```
