```
gebal!(job, A) -> (ilo, ihi, scale)
```

Balancea la matriz `A` antes de calcular su sistema de eigenvalores o la factorización de Schur. `job` puede ser uno de `N` (`A` no será permutada ni escalada), `P` (`A` solo será permutada), `S` (`A` solo será escalada) o `B` (`A` será tanto permutada como escalada). Modifica `A` en su lugar y devuelve `ilo`, `ihi` y `scale`. Si se activó la permutación, `A[i,j] = 0` si `j > i` y `1 < j < ilo` o `j > ihi`. `scale` contiene información sobre la escalación/permutaciones realizadas.
