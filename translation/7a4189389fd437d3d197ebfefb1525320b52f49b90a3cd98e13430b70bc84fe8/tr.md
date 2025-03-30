```
findlast(predicate::Function, A)
```

`predicate` doğru döndüğü `A`'nın son elemanının indeksini veya anahtarını döndürür. Böyle bir eleman yoksa `nothing` döner.

İndeksler veya anahtarlar, [`keys(A)`](@ref) ve [`pairs(A)`](@ref) tarafından döndürülenlerle aynı türdedir.

# Örnekler

```jldoctest
julia> A = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> findlast(isodd, A)
3

julia> findlast(x -> x > 5, A) # nothing döner, ama REPL'de yazdırılmaz

julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> findlast(isodd, A)
CartesianIndex(2, 1)
```
