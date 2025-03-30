```
transpose!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}) where {Tv,Ti}
```

Matris `A`'yı transpoze eder ve sonucu `X` matrisine kaydeder. `size(X)` değeri `size(transpose(A))` ile eşit olmalıdır. Gerekirse yalnızca `X`'in rowval ve nzval'ını yeniden boyutlandırmak dışında ek bellek tahsis edilmez.

`halfperm!`'e bakınız.
