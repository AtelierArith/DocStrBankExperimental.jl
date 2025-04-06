```
pairs(collection)
```

Herhangi bir koleksiyondaki `anahtar => değer` çiftleri üzerinde bir yineleyici döndürür; bu, bir dizi gibi bir anahtar kümesini bir değer kümesine eşleyen koleksiyonları içerir. Anahtarlar dizi indeksleri olduğunda diziler de buna dahildir. Girişler dahili olarak bir hash tablosunda saklandığında, `Dict` gibi, döndürülen sıranın değişebileceğini unutmayın. Ancak `keys(a)`, `values(a)` ve `pairs(a)` hepsi `a` üzerinde yineleme yapar ve öğeleri aynı sırada döndürür.

# Örnekler

```jldoctest
julia> a = Dict(zip(["a", "b", "c"], [1, 2, 3]))
Dict{String, Int64} with 3 entries:
  "c" => 3
  "b" => 2
  "a" => 1

julia> pairs(a)
Dict{String, Int64} with 3 entries:
  "c" => 3
  "b" => 2
  "a" => 1

julia> foreach(println, pairs(["a", "b", "c"]))
1 => "a"
2 => "b"
3 => "c"

julia> (;a=1, b=2, c=3) |> pairs |> collect
3-element Vector{Pair{Symbol, Int64}}:
 :a => 1
 :b => 2
 :c => 3

julia> (;a=1, b=2, c=3) |> collect
3-element Vector{Int64}:
 1
 2
 3
```
