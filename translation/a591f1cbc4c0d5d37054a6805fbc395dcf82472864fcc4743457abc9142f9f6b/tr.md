```
rowvals(A::AbstractSparseMatrixCSC)
```

`A`'n satır indekslerinin bir vektörünü döndürür. Döndürülen vektördeki herhangi bir değişiklik `A`'yı da değiştirecektir. Satır indekslerinin dahili olarak nasıl saklandığına erişim sağlamak, yapısal sıfır olmayan değerler üzerinde yineleme ile birlikte yararlı olabilir. Ayrıca [`nonzeros`](@ref) ve [`nzrange`](@ref) ile de bakılabilir.

# Örnekler

```jldoctest
julia> A = sparse(2I, 3, 3)
3×3 SparseMatrixCSC{Int64, Int64} with 3 stored entries:
 2  ⋅  ⋅
 ⋅  2  ⋅
 ⋅  ⋅  2

julia> rowvals(A)
3-element Vector{Int64}:
 1
 2
 3
```
