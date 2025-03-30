```
findnz(A::SparseMatrixCSC)
```

Sıkıştırılmış matris `A`'deki saklanan ("yapısal sıfır olmayan") değerlerin satır ve sütun indekslerini içeren bir tuple `(I, J, V)` döndürür; burada `I` ve `J` saklanan değerlerin satır ve sütun indeksleridir ve `V` değerlerin bir vektörüdür.

# Örnekler

```jldoctest
julia> A = sparse([1 2 0; 0 0 3; 0 4 0])
3×3 SparseMatrixCSC{Int64, Int64} with 4 stored entries:
 1  2  ⋅
 ⋅  ⋅  3
 ⋅  4  ⋅

julia> findnz(A)
([1, 1, 3, 2], [1, 2, 2, 3], [1, 2, 4, 3])
```
