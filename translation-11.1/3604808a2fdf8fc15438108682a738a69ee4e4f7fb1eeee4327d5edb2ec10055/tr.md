```
pushfirst!(koleksiyon, öğeler...) -> koleksiyon
```

Bir veya daha fazla `öğeyi` koleksiyonun başına ekler.

Bu işlev birçok diğer programlama dilinde `unshift` olarak adlandırılır.

# Örnekler

```jldoctest
julia> pushfirst!([1, 2, 3, 4], 5, 6)
6-element Vector{Int64}:
 5
 6
 1
 2
 3
 4
```
