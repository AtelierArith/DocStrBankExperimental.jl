```
permute!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti},
         p::AbstractVector{<:Integer}, q::AbstractVector{<:Integer},
         [C::AbstractSparseMatrixCSC{Tv,Ti}]) where {Tv,Ti}
```

`A`'yı iki yönlü olarak permütasyon yapar ve sonucu `PAQ` (`A[p,q]`) olarak `X`'e kaydeder. Ara sonucu `(AQ)^T` (`transpose(A[:,q])`) isteğe bağlı argüman `C`'ye kaydeder, eğer mevcutsa. `X`, `A` ve, eğer mevcutsa, `C`'nin birbirine alias olmaması gerekmektedir; sonucu `A`'ya geri kaydetmek için `X`'i içermeyen aşağıdaki yöntemi kullanın:

```
permute!(A::AbstractSparseMatrixCSC{Tv,Ti}, p::AbstractVector{<:Integer},
         q::AbstractVector{<:Integer}[, C::AbstractSparseMatrixCSC{Tv,Ti},
         [workcolptr::Vector{Ti}]]) where {Tv,Ti}
```

`X`'in boyutları `A`'nın boyutlarıyla eşleşmelidir (`size(X, 1) == size(A, 1)` ve `size(X, 2) == size(A, 2)`), ve `X`, `A`'daki tüm tahsis edilmiş girişleri karşılayacak kadar depolama alanına sahip olmalıdır (`length(rowvals(X)) >= nnz(A)` ve `length(nonzeros(X)) >= nnz(A)`). Sütun permütasyonu `q`'nun uzunluğu `A`'nın sütun sayısıyla eşleşmelidir (`length(q) == size(A, 2)`). Satır permütasyonu `p`'nin uzunluğu `A`'nın satır sayısıyla eşleşmelidir (`length(p) == size(A, 1)`).

`C`'nin boyutları `transpose(A)` ile eşleşmelidir (`size(C, 1) == size(A, 2)` ve `size(C, 2) == size(A, 1)`), ve `C`, `A`'daki tüm tahsis edilmiş girişleri karşılayacak kadar depolama alanına sahip olmalıdır (`length(rowvals(C)) >= nnz(A)` ve `length(nonzeros(C)) >= nnz(A)`).

Ek (algoritmik) bilgi için ve argüman kontrolü yapmayan bu yöntemlerin versiyonları için (ihracat dışı) ana yöntemler `unchecked_noalias_permute!` ve `unchecked_aliasing_permute!`'ye bakın.

Ayrıca [`permute`](@ref) ile de bakabilirsiniz.
