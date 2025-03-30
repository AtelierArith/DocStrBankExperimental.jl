```
map(f, c...) -> koleksiyon
```

Koleksiyon `c`'yi her bir elemana `f` uygulayarak dönüştür. Birden fazla koleksiyon argümanı için, `f`'yi eleman bazında uygula ve herhangi biri tükenene kadar dur.

Ayrıca bkz. [`map!`](@ref), [`foreach`](@ref), [`mapreduce`](@ref), [`mapslices`](@ref), [`zip`](@ref), [`Iterators.map`](@ref).

# Örnekler

```jldoctest
julia> map(x -> x * 2, [1, 2, 3])
3-element Vector{Int64}:
 2
 4
 6

julia> map(+, [1, 2, 3], [10, 20, 30, 400, 5000])
3-element Vector{Int64}:
 11
 22
 33
```
