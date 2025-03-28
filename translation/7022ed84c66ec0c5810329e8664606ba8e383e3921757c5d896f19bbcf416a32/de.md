```
geqrt3!(A, T)
```

Berechnet rekursiv die blockierte `QR`-Faktorisierung von `A`, `A = QR`. `T` enthält obere dreieckige Blockreflektoren, die die elementaren Reflektoren der Faktorisierung parametrisieren. Die erste Dimension von `T` legt die Blockgröße fest und muss zwischen 1 und `n` liegen. Die zweite Dimension von `T` muss der kleinsten Dimension von `A` entsprechen.

Gibt `A` und `T` modifiziert in-place zurück.
