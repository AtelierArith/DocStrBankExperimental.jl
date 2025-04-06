```
adjoint!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}) where {Tv,Ti}
```

Matris `A`'nın transpozunu alır ve `X` matrisindeki elemanların adjoint'ini depolar. `size(X)` değeri `size(transpose(A))` ile eşit olmalıdır. `X`'in rowval ve nzval'ını yeniden boyutlandırmak gerekirse, başka bir bellek tahsisi yapılmaz.

`halfperm!`'e bakınız.
