```
gbtrf!(kl, ku, m, AB) -> (AB, ipiv)
```

Berechne die LU-Zerlegung einer bandierten Matrix `AB`. `kl` ist die erste Unterdiagonale, die ein nicht null Band enthält, `ku` ist die letzte Oberdiagonale, die eines enthält, und `m` ist die erste Dimension der Matrix `AB`. Gibt die LU-Zerlegung in-place und `ipiv`, den Vektor der verwendeten Pivots, zurück.
