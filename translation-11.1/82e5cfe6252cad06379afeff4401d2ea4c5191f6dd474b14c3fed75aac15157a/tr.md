```
keepat!(a::Vector, m::AbstractVector{Bool})
keepat!(a::BitVector, m::AbstractVector{Bool})
```

Yerinde mantıksal indeksleme versiyonu `a = a[m]`. Yani, eşit uzunluktaki `a` ve `m` vektörlerinde `keepat!(a, m)` işlemi, `m`'nin karşılık gelen indekste `false` olduğu tüm `a` elemanlarını kaldırır.

# Örnekler

```jldoctest
julia> a = [:a, :b, :c];

julia> keepat!(a, [true, false, true])
2-element Vector{Symbol}:
 :a
 :c

julia> a
2-element Vector{Symbol}:
 :a
 :c
```
