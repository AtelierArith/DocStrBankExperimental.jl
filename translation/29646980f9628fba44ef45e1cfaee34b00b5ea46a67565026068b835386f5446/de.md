```
gehrd!(ilo, ihi, A) -> (A, tau)
```

Konvertiert eine Matrix `A` in Hessenberg-Form. Wenn `A` mit `gebal!` balanciert ist, dann sind `ilo` und `ihi` die Ausgaben von `gebal!`. Andernfalls sollten sie `ilo = 1` und `ihi = size(A,2)` sein. `tau` enthält die elementaren Reflektoren der Faktorisierung.
