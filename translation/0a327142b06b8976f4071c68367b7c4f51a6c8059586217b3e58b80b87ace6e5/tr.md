```
findnext(predicate::Function, A, i)
```

`predicate`'in `true` döndüğü `A`'nın bir elemanının `i`'den sonraki veya `i` dahil indeksini bulur, eğer bulunamazsa `nothing` döner. Bu, [`getindex`](@ref), [`keys(A)`](@ref) ve [`nextind`](@ref) destekleyen Diziler, String'ler ve diğer çoğu koleksiyon için çalışır.

İndeksler, [`keys(A)`](@ref) ve [`pairs(A)`](@ref) tarafından döndürülenlerle aynı türdedir.

# Örnekler

```jldoctest
julia> A = [1, 4, 2, 2];

julia> findnext(isodd, A, 1)
1

julia> findnext(isodd, A, 2) # nothing döner, ama REPL'de yazdırılmaz

julia> A = [1 4; 2 2];

julia> findnext(isodd, A, CartesianIndex(1, 1))
CartesianIndex(1, 1)

julia> findnext(isspace, "a b c", 3)
4
```
