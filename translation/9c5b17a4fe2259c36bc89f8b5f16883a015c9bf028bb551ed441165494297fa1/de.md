```
getri!(A, ipiv)
```

Berechnet die Inverse von `A`, unter Verwendung seiner `LU`-Faktorisierung, die von `getrf!` gefunden wurde. `ipiv` ist die Pivot-Informationsausgabe und `A` enthält die `LU`-Faktorisierung von `getrf!`. `A` wird mit seiner Inversen überschrieben.
