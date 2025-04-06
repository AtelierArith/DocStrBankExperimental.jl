```
filter!(f, a)
```

Koleksiyonu `a` güncelleyin, `f`'nin `false` olduğu elemanları kaldırın. `f` fonksiyonuna bir argüman geçilir.

# Örnekler

```jldoctest
julia> filter!(isodd, Vector(1:10))
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
