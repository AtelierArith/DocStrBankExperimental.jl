```
gesdd!(iş, A) -> (U, S, VT)
```

`A`'nın tekil değer ayrıştırmasını bulur, `A = U * S * V'`, böl ve fethet yaklaşımını kullanarak. Eğer `iş = A` ise, `U`'nun tüm sütunları ve `V'`nin satırları hesaplanır. Eğer `iş = N` ise, `U`'nun sütunları veya `V'`nin satırları hesaplanmaz. Eğer `iş = O` ise, `A` (ince) `U`'nun sütunları ve (ince) `V'`nin satırları ile üzerine yazılır. Eğer `iş = S` ise, (ince) `U`'nun sütunları ve (ince) `V'`nin satırları hesaplanır ve ayrı olarak döndürülür.
