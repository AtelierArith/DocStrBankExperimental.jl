```
geqrt3!(A) -> (A, T)
```

Berechnet rekursiv die blockierte `QR`-Faktorisierung von `A`, `A = QR`.

Gibt `A` zurück, das in-place modifiziert wurde, und `T`, das obere dreieckige Blockreflektoren enthält, die die elementaren Reflektoren der Faktorisierung parametrisieren.
