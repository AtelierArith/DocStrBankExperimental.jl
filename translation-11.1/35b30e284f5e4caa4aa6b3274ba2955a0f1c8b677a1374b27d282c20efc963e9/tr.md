```
prepend!(a::Vector, collections...) -> collection
```

Her `collections` içindeki her bir öğeyi `a`'nın başına ekleyin.

`collections` birden fazla koleksiyon belirttiğinde, sıralama korunur: `collections[1]`'in öğeleri `a`'da en solda yer alacak ve devam edecektir.

!!! compat "Julia 1.6"
    Birden fazla koleksiyonun eklenmesi, en az Julia 1.6 gerektirir.


# Örnekler

```jldoctest
julia> prepend!([3], [1, 2])
3-element Vector{Int64}:
 1
 2
 3

julia> prepend!([6], [1, 2], [3, 4, 5])
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6
```
