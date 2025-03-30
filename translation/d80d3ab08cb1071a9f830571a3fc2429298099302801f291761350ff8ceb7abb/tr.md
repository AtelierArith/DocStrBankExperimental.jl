```
dropzeros(A::AbstractSparseMatrixCSC;)
```

`A`'nın bir kopyasını oluşturur ve o kopyadan saklanan sayısal sıfırları kaldırır.

Yerinde bir versiyon ve algoritmik bilgi için [`dropzeros!`](@ref) kısmına bakın.

# Örnekler

```jldoctest
julia> A = sparse([1, 2, 3], [1, 2, 3], [1.0, 0.0, 1.0])
3×3 SparseMatrixCSC{Float64, Int64} ile 3 saklanan girdi:
 1.0   ⋅    ⋅
  ⋅   0.0   ⋅
  ⋅    ⋅   1.0

julia> dropzeros(A)
3×3 SparseMatrixCSC{Float64, Int64} ile 2 saklanan girdi:
 1.0   ⋅    ⋅
  ⋅    ⋅    ⋅
  ⋅    ⋅   1.0
```
