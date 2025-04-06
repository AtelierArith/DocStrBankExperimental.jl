```
sparsevec(d::Dict, [m])
```

`m` uzunluğunda, sıfır olmayan indekslerin anahtarları sözlükten ve sıfır olmayan değerlerin sözlükten değerler olduğu seyrek bir vektör oluşturur.

# Örnekler

```jldoctest
julia> sparsevec(Dict(1 => 3, 2 => 2))
2-element SparseVector{Int64, Int64} with 2 stored entries:
  [1]  =  3
  [2]  =  2
```
