```
Perm(order::Ordering, data::AbstractVector)
```

`Ordering` sur les indices de `data` où `i` est inférieur à `j` si `data[i]` est inférieur à `data[j]` selon `order`. Dans le cas où `data[i]` et `data[j]` sont égaux, `i` et `j` sont comparés par valeur numérique.
