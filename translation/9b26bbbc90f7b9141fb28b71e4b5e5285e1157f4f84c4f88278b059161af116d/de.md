```
geqrt!(A, nb) -> (A, T)
```

Berechne die blockierte `QR`-Faktorisierung von `A`, `A = QR`. `nb` legt die Blockgröße fest und muss zwischen 1 und `n`, der zweiten Dimension von `A`, liegen.

Gibt `A` zurück, das in-place modifiziert wurde, und `T`, das obere dreieckige Blockreflektoren enthält, die die elementaren Reflektoren der Faktorisierung parametrisieren.
