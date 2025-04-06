```
findnext(A, i)
```

`A` içindeki `true` elemanının `i`'den sonraki veya `i` dahil indeksini bulur, eğer bulunamazsa `nothing` döner.

İndeksler, [`keys(A)`](@ref) ve [`pairs(A)`](@ref) tarafından döndürülenlerle aynı türdedir.

# Örnekler

```jldoctest
julia> A = [false, false, true, false]
4-element Vector{Bool}:
 0
 0
 1
 0

julia> findnext(A, 1)
3

julia> findnext(A, 4) # bulunamaz, ancak REPL'de yazdırılmaz

julia> A = [false false; true false]
2×2 Matrix{Bool}:
 0  0
 1  0

julia> findnext(A, CartesianIndex(1, 1))
CartesianIndex(2, 1)
```
