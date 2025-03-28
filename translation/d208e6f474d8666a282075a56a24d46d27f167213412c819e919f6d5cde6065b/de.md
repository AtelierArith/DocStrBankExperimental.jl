```
trsyl!(transa, transb, A, B, C, isgn=1) -> (C, scale)
```

Löst die Sylvester-Matrixgleichung `A * X +/- X * B = scale*C`, wobei `A` und `B` beide quasi-obere dreieckige Matrizen sind. Wenn `transa = N`, wird `A` nicht modifiziert. Wenn `transa = T`, wird `A` transponiert. Wenn `transa = C`, wird `A` konjugiert transponiert. Ähnlich für `transb` und `B`. Wenn `isgn = 1`, wird die Gleichung `A * X + X * B = scale * C` gelöst. Wenn `isgn = -1`, wird die Gleichung `A * X - X * B = scale * C` gelöst.

Gibt `X` (überschreibt `C`) und `scale` zurück.
