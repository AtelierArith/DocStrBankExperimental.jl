```
ggsvd!(jobu, jobv, jobq, A, B) -> (U, V, Q, alpha, beta, k, l, R)
```

Trouve la décomposition en valeurs singulières généralisées de `A` et `B`, `U'*A*Q = D1*R` et `V'*B*Q = D2*R`. `D1` a `alpha` sur sa diagonale et `D2` a `beta` sur sa diagonale. Si `jobu = U`, la matrice orthogonale/unitaire `U` est calculée. Si `jobv = V`, la matrice orthogonale/unitaire `V` est calculée. Si `jobq = Q`, la matrice orthogonale/unitaire `Q` est calculée. Si `jobu`, `jobv` ou `jobq` est `N`, cette matrice n'est pas calculée. Cette fonction n'est disponible que dans les versions de LAPACK antérieures à 3.6.0.
