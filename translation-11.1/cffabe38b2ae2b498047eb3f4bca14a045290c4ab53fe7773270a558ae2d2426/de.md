```
hseqr!(job, compz, ilo, ihi, H, Z) -> (H, Z, w)
```

Berechnet alle Eigenwerte und (optional) die Schur-Faktorisierung einer Matrix, die auf Hessenberg-Form reduziert ist. Wenn `H` mit `gebal!` balanciert ist, dann sind `ilo` und `ihi` die Ausgaben von `gebal!`. Andernfalls sollten sie `ilo = 1` und `ihi = size(H,2)` sein. `tau` enthält die elementaren Reflektoren der Faktorisierung.
