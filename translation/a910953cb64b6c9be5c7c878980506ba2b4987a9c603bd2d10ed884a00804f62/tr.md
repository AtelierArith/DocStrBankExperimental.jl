```
rest(iter, state)
```

Verilen `state`'den başlayarak `iter` ile aynı öğeleri veren bir yineleyici.

Ayrıca bakınız: [`Iterators.drop`](@ref), [`Iterators.peel`](@ref), [`Base.rest`](@ref).

# Örnekler

```jldoctest
julia> collect(Iterators.rest([1,2,3,4], 2))
3-element Vector{Int64}:
 2
 3
 4
```
