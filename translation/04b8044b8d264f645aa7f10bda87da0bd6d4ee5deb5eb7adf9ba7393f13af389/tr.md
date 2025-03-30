```
values(a::AbstractDict)
```

Bir koleksiyondaki tüm değerler üzerinde bir yineleyici döndürür. `collect(values(a))` bir değerler dizisi döndürür. Değerler bir hash tablosunda saklandığında, `Dict` durumunda olduğu gibi, döndürülen sıranın değişebileceğini unutmayın. Ancak `keys(a)`, `values(a)` ve `pairs(a)` hepsi `a` üzerinde yineleme yapar ve elemanları aynı sırada döndürür.

# Örnekler

```jldoctest
julia> D = Dict('a'=>2, 'b'=>3)
Dict{Char, Int64} with 2 entries:
  'a' => 2
  'b' => 3

julia> collect(values(D))
2-element Vector{Int64}:
 2
 3
```
