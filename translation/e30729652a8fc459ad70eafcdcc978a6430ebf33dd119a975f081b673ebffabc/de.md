```
gbtrs!(trans, kl, ku, m, AB, ipiv, B)
```

Lösen Sie die Gleichung `AB * X = B`. `trans` bestimmt die Ausrichtung von `AB`. Es kann `N` (keine Transponierung), `T` (Transponierung) oder `C` (konjugierte Transponierung) sein. `kl` ist die erste Unterdiagonale, die ein von Null verschiedenes Band enthält, `ku` ist die letzte Oberdiagonale, die eines enthält, und `m` ist die erste Dimension der Matrix `AB`. `ipiv` ist der Vektor der Pivots, der von `gbtrf!` zurückgegeben wird. Gibt den Vektor oder die Matrix `X` zurück und überschreibt `B` vor Ort.
