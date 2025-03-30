```
findprev(A, i)
```

`A` içindeki `true` elemanının `i`'den önceki veya `i` dahil indeksini bulur, eğer bulunamazsa `nothing` döner.

İndeksler, [`keys(A)`](@ref) ve [`pairs(A)`](@ref) tarafından döndürülenlerle aynı türdedir.

Ayrıca bakınız: [`findnext`](@ref), [`findfirst`](@ref), [`findall`](@ref).

# Örnekler

```jldoctest
julia> A = [false, false, true, true]
4-element Vector{Bool}:
 0
 0
 1
 1

julia> findprev(A, 3)
3

julia> findprev(A, 1) # hiçbir şey döner, ancak REPL'de yazdırılmaz

julia> A = [false false; true true]
2×2 Matrix{Bool}:
 0  0
 1  1

julia> findprev(A, CartesianIndex(2, 1))
CartesianIndex(2, 1)
```
