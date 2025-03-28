```
ggsvd3!(jobu, jobv, jobq, A, B) -> (U, V, Q, alpha, beta, k, l, R)
```

Findet die verallgemeinerte singuläre Wertzerlegung von `A` und `B`, `U'*A*Q = D1*R` und `V'*B*Q = D2*R`. `D1` hat `alpha` auf seiner Diagonalen und `D2` hat `beta` auf seiner Diagonalen. Wenn `jobu = U`, wird die orthogonale/einheitliche Matrix `U` berechnet. Wenn `jobv = V`, wird die orthogonale/einheitliche Matrix `V` berechnet. Wenn `jobq = Q`, wird die orthogonale/einheitliche Matrix `Q` berechnet. Wenn `jobu`, `jobv` oder `jobq` `N` ist, wird diese Matrix nicht berechnet. Diese Funktion erfordert LAPACK 3.6.0.
