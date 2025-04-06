```
findfirst(predicate::Function, A)
```

`predicate` doğru döndüğü `A`'nın ilk elemanının indeksini veya anahtarını döndürür. Böyle bir eleman yoksa `nothing` döner.

İndeksler veya anahtarlar, [`keys(A)`](@ref) ve [`pairs(A)`](@ref) tarafından döndürülenlerle aynı türdedir.

# Örnekler

```jldoctest
julia> A = [1, 4, 2, 2]
4-element Vector{Int64}:
 1
 4
 2
 2

julia> findfirst(iseven, A)
2

julia> findfirst(x -> x>10, A) # hiçbir şey döndürmez, ancak REPL'de yazdırılmaz

julia> findfirst(isequal(4), A)
2

julia> A = [1 4; 2 2]
2×2 Matrix{Int64}:
 1  4
 2  2

julia> findfirst(iseven, A)
CartesianIndex(2, 1)
```
