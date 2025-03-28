```
lowrankupdate!(C::Cholesky, v::AbstractVector) -> CC::Cholesky
```

Aktualisiert eine Cholesky-Faktorisierung `C` mit dem Vektor `v`. Wenn `A = C.U'C.U` dann ist `CC = cholesky(C.U'C.U + v*v')`, aber die Berechnung von `CC` verwendet nur `O(n^2)` Operationen. Die Eingabefaktorisierung `C` wird vor Ort aktualisiert, sodass beim Verlassen `C == CC` gilt. Der Vektor `v` wird während der Berechnung zerstört.
