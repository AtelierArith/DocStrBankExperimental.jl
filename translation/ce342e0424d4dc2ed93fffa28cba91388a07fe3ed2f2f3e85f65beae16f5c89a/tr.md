```
ggsvd3!(jobu, jobv, jobq, A, B) -> (U, V, Q, alpha, beta, k, l, R)
```

`A` ve `B`'nin genelleştirilmiş tekil değer ayrıştırmasını bulur, `U'*A*Q = D1*R` ve `V'*B*Q = D2*R`. `D1`'in köşegeninde `alpha`, `D2`'nin köşegeninde ise `beta` bulunur. Eğer `jobu = U` ise, ortogonal/birlikte matris `U` hesaplanır. Eğer `jobv = V` ise ortogonal/birlikte matris `V` hesaplanır. Eğer `jobq = Q` ise ortogonal/birlikte matris `Q` hesaplanır. Eğer `jobu`, `jobv` veya `jobq` `N` ise, o matris hesaplanmaz. Bu fonksiyon LAPACK 3.6.0 gerektirir.
