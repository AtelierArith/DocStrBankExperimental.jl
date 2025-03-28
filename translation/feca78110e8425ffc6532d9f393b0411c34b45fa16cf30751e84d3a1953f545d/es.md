```
Perm(order::Ordering, data::AbstractVector)
```

`Ordering` en los índices de `data` donde `i` es menor que `j` si `data[i]` es menor que `data[j]` de acuerdo con `order`. En el caso de que `data[i]` y `data[j]` sean iguales, `i` y `j` se comparan por valor numérico.
