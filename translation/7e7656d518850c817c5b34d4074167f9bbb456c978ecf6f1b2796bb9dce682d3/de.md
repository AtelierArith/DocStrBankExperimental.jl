```
rank(S::SparseMatrixCSC{Tv,Ti}; [tol::Real]) -> Ti
```

Berechne den Rang von `S`, indem du seine QR-Zerlegung berechnest. Werte kleiner als `tol` werden als null betrachtet. Siehe das Handbuch von SPQR.
