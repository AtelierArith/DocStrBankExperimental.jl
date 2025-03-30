```
rank(S::SparseMatrixCSC{Tv,Ti}; [tol::Real]) -> Ti
```

`S`'nin sıralamasını, QR faktörizasyonunu hesaplayarak hesaplayın. `tol`'dan daha küçük değerler sıfır olarak kabul edilir. SPQR'nin kılavuzuna bakın.
