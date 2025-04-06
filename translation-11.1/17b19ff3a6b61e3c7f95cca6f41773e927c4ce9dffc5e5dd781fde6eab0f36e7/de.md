```
gesv!(A, B) -> (B, A, ipiv)
```

Löst die lineare Gleichung `A * X = B`, wobei `A` eine quadratische Matrix ist, unter Verwendung der `LU`-Faktorisierung von `A`. `A` wird mit seiner `LU`-Faktorisierung überschrieben und `B` wird mit der Lösung `X` überschrieben. `ipiv` enthält die Pivotierungsinformationen für die `LU`-Faktorisierung von `A`.
