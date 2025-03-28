```
gebrd!(A) -> (A, d, e, tauq, taup)
```

Reduziert `A` in-place auf bidiagonale Form `A = QBP'`. Gibt `A` zurück, das die bidiagonale Matrix `B` enthält; `d`, das die Diagonalelemente von `B` enthält; `e`, das die Nebendiagonalelemente von `B` enthält; `tauq`, das die elementaren Reflektoren darstellt, die `Q` repräsentieren; und `taup`, das die elementaren Reflektoren darstellt, die `P` repräsentieren.
