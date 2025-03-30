```
first(itr, n::Integer)
```

İterable koleksiyon `itr`'nin ilk `n` elemanını alır veya `itr` yeterince uzun değilse daha az eleman alır.

Ayrıca bakınız: [`startswith`](@ref), [`Iterators.take`](@ref).

!!! compat "Julia 1.6"
    Bu yöntem en az Julia 1.6 gerektirir.


# Örnekler

```jldoctest
julia> first(["foo", "bar", "qux"], 2)
2-element Vector{String}:
 "foo"
 "bar"

julia> first(1:6, 10)
1:6

julia> first(Bool[], 1)
Bool[]
```
