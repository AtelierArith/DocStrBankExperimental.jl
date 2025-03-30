```
setindex!(collection, value, key...)
```

Verilen değeri bir koleksiyondaki belirtilen anahtar veya indeks içinde saklayın. `a[i,j,...] = x` sözdizimi derleyici tarafından `(setindex!(a, x, i, j, ...); x)` şeklinde dönüştürülür.

# Örnekler

```jldoctest
julia> a = Dict("a"=>1)
Dict{String, Int64} with 1 entry:
  "a" => 1

julia> setindex!(a, 2, "b")
Dict{String, Int64} with 2 entries:
  "b" => 2
  "a" => 1
```
