```
gesvd!(jobu, jobvt, A) -> (U, S, VT)
```

`A`'nın tekil değer ayrıştırmasını bulur, `A = U * S * V'`. Eğer `jobu = A` ise, `U`'nun tüm sütunları hesaplanır. Eğer `jobvt = A` ise, `V'`nin tüm satırları hesaplanır. Eğer `jobu = N` ise, `U`'nun sütunları hesaplanmaz. Eğer `jobvt = N` ise, `V'`nin satırları hesaplanmaz. Eğer `jobu = O` ise, `A` (ince) `U`'nun sütunları ile üzerine yazılır. Eğer `jobvt = O` ise, `A` (ince) `V'`nin satırları ile üzerine yazılır. Eğer `jobu = S` ise, (ince) `U`'nun sütunları hesaplanır ve ayrı olarak döndürülür. Eğer `jobvt = S` ise, (ince) `V'`nin satırları hesaplanır ve ayrı olarak döndürülür. `jobu` ve `jobvt` ikisi birden `O` olamaz.

`U`, `S` ve `Vt`'yi döndürür, burada `S`, `A`'nın tekil değerleridir.
