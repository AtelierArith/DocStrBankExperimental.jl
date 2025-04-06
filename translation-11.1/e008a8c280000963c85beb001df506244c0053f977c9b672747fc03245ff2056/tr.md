```
indexin(a, b)
```

`b` içinde bir üye olan `a`'daki her değer için `b`'deki ilk indeksi içeren bir dizi döndürür. Çıktı dizisi, `a`'nın `b`'nin bir üyesi olmadığı yerlerde `nothing` içerir.

Ayrıca bakınız: [`sortperm`](@ref), [`findfirst`](@ref).

# Örnekler

```jldoctest
julia> a = ['a', 'b', 'c', 'b', 'd', 'a'];

julia> b = ['a', 'b', 'c'];

julia> indexin(a, b)
6-element Vector{Union{Nothing, Int64}}:
 1
 2
 3
 2
  nothing
 1

julia> indexin(b, a)
3-element Vector{Union{Nothing, Int64}}:
 1
 2
 3
```
