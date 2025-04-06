```
lowrankdowndate(C::Cholesky, v::AbstractVector) -> CC::Cholesky
```

Führen Sie eine Downdate einer Cholesky-Faktorisierung `C` mit dem Vektor `v` durch. Wenn `A = C.U'C.U` dann ist `CC = cholesky(C.U'C.U - v*v')`, aber die Berechnung von `CC` verwendet nur `O(n^2)` Operationen.
