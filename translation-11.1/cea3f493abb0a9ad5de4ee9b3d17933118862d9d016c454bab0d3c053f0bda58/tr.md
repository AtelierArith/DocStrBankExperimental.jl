```
findprev(predicate::Function, A, i)
```

`predicate` doğru döndüren `A`'nın `i`'den önceki veya `i` dahilindeki bir elemanının önceki indeksini bulur, eğer bulunamazsa `nothing` döner. Bu, [`getindex`](@ref), [`keys(A)`](@ref) ve [`nextind`](@ref) destekleyen Diziler, String'ler ve diğer çoğu koleksiyon için çalışır.

İndeksler, [`keys(A)`](@ref) ve [`pairs(A)`](@ref) tarafından döndürülenlerle aynı türdedir.

# Örnekler

```jldoctest
julia> A = [4, 6, 1, 2]
4-element Vector{Int64}:
 4
 6
 1
 2

julia> findprev(isodd, A, 1) # hiçbir şey döner, ancak REPL'de yazdırılmaz

julia> findprev(isodd, A, 3)
3

julia> A = [4 6; 1 2]
2×2 Matrix{Int64}:
 4  6
 1  2

julia> findprev(isodd, A, CartesianIndex(1, 2))
CartesianIndex(2, 1)

julia> findprev(isspace, "a b c", 3)
2
```
