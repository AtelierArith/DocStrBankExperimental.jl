```
ggsvd3!(jobu, jobv, jobq, A, B) -> (U, V, Q, alpha, beta, k, l, R)
```

Encuentra la descomposición en valores singulares generalizada de `A` y `B`, `U'*A*Q = D1*R` y `V'*B*Q = D2*R`. `D1` tiene `alpha` en su diagonal y `D2` tiene `beta` en su diagonal. Si `jobu = U`, se calcula la matriz ortogonal/unitaria `U`. Si `jobv = V`, se calcula la matriz ortogonal/unitaria `V`. Si `jobq = Q`, se calcula la matriz ortogonal/unitaria `Q`. Si `jobu`, `jobv` o `jobq` es `N`, esa matriz no se calcula. Esta función requiere LAPACK 3.6.0.
