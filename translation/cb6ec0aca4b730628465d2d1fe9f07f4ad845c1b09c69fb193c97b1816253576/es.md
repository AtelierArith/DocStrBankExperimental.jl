```
gebrd!(A) -> (A, d, e, tauq, taup)
```

Reduce `A` in-place to bidiagonal form `A = QBP'`. Returns `A`, que contiene la matriz bidiagonal `B`; `d`, que contiene los elementos diagonales de `B`; `e`, que contiene los elementos fuera de la diagonal de `B`; `tauq`, que contiene los reflectores elementales que representan `Q`; y `taup`, que contiene los reflectores elementales que representan `P`.
