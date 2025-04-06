```
collect(element_type, collection)
```

Verilen eleman türüne sahip bir `Array` döndürür, bu da bir koleksiyondaki veya yineleyicideki tüm öğeleri içerir. Sonuç, `collection` ile aynı şekle ve boyut sayısına sahiptir.

# Örnekler

```jldoctest
julia> collect(Float64, 1:2:5)
3-element Vector{Float64}:
 1.0
 3.0
 5.0
```
