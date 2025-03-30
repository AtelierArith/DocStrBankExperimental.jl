```
symdiff(s, itrs...)
```

Geçilen kümelerdeki elemanların simetrik farkını oluşturur. `s` bir `AbstractSet` değilse, sıralama korunur.

Ayrıca bkz. [`symdiff!`](@ref), [`setdiff`](@ref), [`union`](@ref) ve [`intersect`](@ref).

# Örnekler

```jldoctest
julia> symdiff([1,2,3], [3,4,5], [4,5,6])
3-element Vector{Int64}:
 1
 2
 6

julia> symdiff([1,2,1], [2, 1, 2])
Int64[]
```
