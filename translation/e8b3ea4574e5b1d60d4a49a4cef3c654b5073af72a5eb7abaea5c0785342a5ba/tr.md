```
values(iterator)
```

Anahtarları ve değerleri olan bir iterator veya koleksiyon için, değerlere yönelik bir iterator döndürür. Bu fonksiyon, genel bir iteratorun elemanları genellikle "değerleri" olarak kabul edildiğinden, varsayılan olarak argümanını basitçe döndürür.

# Örnekler

```jldoctest
julia> d = Dict("a"=>1, "b"=>2);

julia> values(d)
ValueIterator for a Dict{String, Int64} with 2 entries. Values:
  2
  1

julia> values([2])
1-element Vector{Int64}:
 2
```
