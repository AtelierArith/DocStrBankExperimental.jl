```
last(itr, n::Integer)
```

İterable koleksiyon `itr`'nin son `n` elemanını alır veya `itr` yeterince uzun değilse daha az eleman alır.

!!! compat "Julia 1.6"
    Bu yöntem en az Julia 1.6 gerektirir.


# Örnekler

```jldoctest
julia> last(["foo", "bar", "qux"], 2)
2-element Vector{String}:
 "bar"
 "qux"

julia> last(1:6, 10)
1:6

julia> last(Float64[], 1)
Float64[]
```
