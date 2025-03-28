```
getrf!(A) -> (A, ipiv, info)
```

Berechne die pivotierte `LU`-Faktorisierung von `A`, `A = LU`.

Gibt `A` zurück, das in-place modifiziert wurde, `ipiv`, die Pivotierungsinformationen, und einen `info`-Code, der den Erfolg anzeigt (`info = 0`), einen singulären Wert in `U` (`info = i`, in diesem Fall ist `U[i,i]` singulär) oder einen Fehlercode (`info < 0`).
