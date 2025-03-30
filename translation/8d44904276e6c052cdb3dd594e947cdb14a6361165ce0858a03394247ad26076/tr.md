```
chop(s::AbstractString; head::Integer = 0, tail::Integer = 1)
```

`s`'den ilk `head` ve son `tail` karakterlerini kaldırır. `chop(s)` çağrısı `s`'den son karakteri kaldırır. Eğer `length(s)`'den daha fazla karakter kaldırılması isteniyorsa, boş bir dize döndürülür.

Ayrıca bkz. [`chomp`](@ref), [`startswith`](@ref), [`first`](@ref).

# Örnekler

```jldoctest
julia> a = "Mart"
"Mart"

julia> chop(a)
"Mar"

julia> chop(a, head = 1, tail = 2)
"ar"

julia> chop(a, head = 5, tail = 5)
""
```
