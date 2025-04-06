```
trexc!(compq, ifst, ilst, T, Q) -> (T, Q)
trexc!(ifst, ilst, T, Q) -> (T, Q)
```

Ordnen Sie die Schur-Faktorisierung `T` einer Matrix neu, sodass der diagonale Block von `T` mit der Zeilenindex `ifst` an die Zeilenindex `ilst` verschoben wird. Wenn `compq = V`, werden die Schur-Vektoren `Q` neu angeordnet. Wenn `compq = N`, werden sie nicht modifiziert. Die 4-Argumente-Methode ruft die 5-Argumente-Methode mit `compq = V` auf.
