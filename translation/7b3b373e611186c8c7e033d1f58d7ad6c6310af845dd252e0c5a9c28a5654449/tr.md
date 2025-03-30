```
halfperm!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{TvA,Ti},
          q::AbstractVector{<:Integer}, f::Function = identity) where {Tv,TvA,Ti}
```

`A`'yı sütun-permute edip transpoze edin, aynı zamanda `A`'nın her bir girişine `f` uygulayın ve sonucu `X`'te saklayın `(f(A)Q)^T` (`map(f, transpose(A[:,q]))`).

`X`'in eleman tipi `Tv`, `A`'nın eleman tipi `TvA` ile eşleşmelidir. `X`'in boyutları `transpose(A)`'nın boyutlarıyla eşleşmelidir (`size(X, 1) == size(A, 2)` ve `size(X, 2) == size(A, 1)`), ayrıca `X`, `A`'da tahsis edilen tüm girişleri karşılayacak kadar depolama alanına sahip olmalıdır (`length(rowvals(X)) >= nnz(A)` ve `length(nonzeros(X)) >= nnz(A)`). Sütun-permutasyon `q`'nun uzunluğu `A`'nın sütun sayısıyla eşleşmelidir (`length(q) == size(A, 2)`).

Bu yöntem, [`SparseMatrixCSC`](@ref) üzerinde transpozisyon ve permütasyon işlemleri gerçekleştiren birkaç yöntemin ana yöntemidir. Bu yöntem argüman kontrolü yapmadığı için, doğrudan kullanıma tercih edilen daha güvenli alt yöntemleri (`[c]transpose[!]`, `permute[!]`) kullanın.

Bu yöntem, F. Gustavson'un "Sparse Matrisler için iki hızlı algoritma: çarpma ve permütasyon transpozisyonu," ACM TOMS 4(3), 250-269 (1978) adlı eserinde tanımlanan `HALFPERM` algoritmasını uygular. Algoritma `O(size(A, 1), size(A, 2), nnz(A))` zamanında çalışır ve geçilenlerden başka bir alan gerektirmez.
