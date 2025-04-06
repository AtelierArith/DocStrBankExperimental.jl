```
sparsevec(I, V, [m, combine])
```

`S` uzunluğunda bir seyrek vektör oluşturur `m` böylece `S[I[k]] = V[k]`. Tekrar edenler `combine` fonksiyonu kullanılarak birleştirilir; eğer `combine` argümanı sağlanmazsa varsayılan olarak `+` kullanılır, `V`'nin elemanları Boolean ise `combine` varsayılan olarak `|` olur.

# Örnekler

```jldoctest
julia> II = [1, 3, 3, 5]; V = [0.1, 0.2, 0.3, 0.2];

julia> sparsevec(II, V)
5-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  0.1
  [3]  =  0.5
  [5]  =  0.2

julia> sparsevec(II, V, 8, -)
8-element SparseVector{Float64, Int64} with 3 stored entries:
  [1]  =  0.1
  [3]  =  -0.1
  [5]  =  0.2

julia> sparsevec([1, 3, 1, 2, 2], [true, true, false, false, false])
3-element SparseVector{Bool, Int64} with 3 stored entries:
  [1]  =  1
  [2]  =  0
  [3]  =  1
```
