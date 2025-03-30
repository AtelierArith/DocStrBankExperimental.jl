```
gecon!(normtype, A, anorm)
```

Matris `A`'nın ters koşul sayısını bulur. Eğer `normtype = I` ise, koşul sayısı sonsuz normda bulunur. Eğer `normtype = O` veya `1` ise, koşul sayısı bir normda bulunur. `A`, `getrf!`'nin sonucu olmalı ve `anorm`, ilgili normda `A`'nın normudur.
