```
lowrankdowndate(C::Cholesky, v::AbstractVector) -> CC::Cholesky
```

Bir Cholesky faktörizasyonunu `C` vektörü `v` ile güncelleyin. Eğer `A = C.U'C.U` ise, `CC = cholesky(C.U'C.U - v*v')` ancak `CC`'nin hesaplanması yalnızca `O(n^2)` işlemi kullanır.
