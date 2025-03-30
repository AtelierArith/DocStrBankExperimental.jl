```
ftranspose!(X::AbstractSparseMatrixCSC{Tv,Ti}, A::AbstractSparseMatrixCSC{Tv,Ti}, f::Function) where {Tv,Ti}
```

`A`'yı transpoze edin ve `f` fonksiyonunu sıfır olmayan elemanlara uygulayarak `X`'e kaydedin. `f` tarafından oluşturulan sıfırları kaldırmaz. `size(X)` `size(transpose(A))` ile eşit olmalıdır. Gerekirse yalnızca `X`'in rowval ve nzval'ını yeniden boyutlandırarak ek bellek tahsis edilmez.

`halfperm!`'e bakın.
