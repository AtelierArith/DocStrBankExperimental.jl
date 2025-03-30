```
parent(A)
```

Görünümün temel ebeveyn nesnesini döndürür. `SubArray`, `SubString`, `ReshapedArray` veya `LinearAlgebra.Transpose` türündeki nesnelerin ebeveyni, nesne oluşturulurken `view`, `reshape`, `transpose` vb. için bir argüman olarak geçirilen nesnedir. Girdi bir sarmalanmış nesne değilse, girdiyi kendisi olarak döndürün. Girdi birden fazla kez sarılmışsa, yalnızca en dıştaki sarıcı kaldırılacaktır.

# Örnekler

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> V = view(A, 1:2, :)
2×2 view(::Matrix{Int64}, 1:2, :) with eltype Int64:
 1  2
 3  4

julia> parent(V)
2×2 Matrix{Int64}:
 1  2
 3  4
```
