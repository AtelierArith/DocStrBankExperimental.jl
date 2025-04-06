```
Perm(order::Ordering, data::AbstractVector)
```

`Ordering` auf den Indizes von `data`, wobei `i` kleiner als `j` ist, wenn `data[i]` kleiner als `data[j]` gemäß `order` ist. Im Fall, dass `data[i]` und `data[j]` gleich sind, werden `i` und `j` nach ihrem numerischen Wert verglichen.
