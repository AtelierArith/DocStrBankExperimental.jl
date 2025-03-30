```
rank(S::SparseMatrixCSC{Tv,Ti}; [tol::Real]) -> Ti
```

`S`의 랭크를 QR 분해를 통해 계산합니다. `tol`보다 작은 값은 0으로 간주됩니다. SPQR 매뉴얼을 참조하세요.
