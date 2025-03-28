```
getrs!(trans, A, ipiv, B)
```

Löst die lineare Gleichung `A * X = B`, `transpose(A) * X = B` oder `adjoint(A) * X = B` für quadratische `A`. Modifiziert die Matrix/Vektor `B` vor Ort mit der Lösung. `A` ist die `LU`-Faktorisierung von `getrf!`, wobei `ipiv` die Pivotierungsinformationen sind. `trans` kann eines von `N` (keine Modifikation), `T` (Transponierte) oder `C` (konjugierte Transponierte) sein.
