```
rank(S::SparseMatrixCSC{Tv,Ti}; [tol::Real]) -> Ti
```

Calcule le rang de `S` en calculant sa factorisation QR. Les valeurs inférieures à `tol` sont considérées comme nulles. Voir le manuel de SPQR.
