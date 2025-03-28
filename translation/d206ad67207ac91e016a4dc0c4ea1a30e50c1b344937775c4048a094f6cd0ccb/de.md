```
getrf!(A, ipiv) -> (A, ipiv, info)
```

Berechne die pivotierte `LU`-Faktorisierung von `A`, `A = LU`. `ipiv` enthält die Pivotierungsinformationen und `info` einen Code, der den Erfolg anzeigt (`info = 0`), einen singulären Wert in `U` (`info = i`, in diesem Fall ist `U[i,i]` singulär) oder einen Fehlercode (`info < 0`).
