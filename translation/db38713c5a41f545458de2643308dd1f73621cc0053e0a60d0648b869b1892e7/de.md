```
gebal!(job, A) -> (ilo, ihi, scale)
```

Balanciere die Matrix `A`, bevor du ihr Eigenwertsystem oder die Schur-Faktorisierung berechnest. `job` kann eines von `N` (`A` wird nicht permutiert oder skaliert), `P` (`A` wird nur permutiert), `S` (`A` wird nur skaliert) oder `B` (`A` wird sowohl permutiert als auch skaliert) sein. Modifiziert `A` in-place und gibt `ilo`, `ihi` und `scale` zurück. Wenn die Permutation aktiviert wurde, gilt `A[i,j] = 0`, wenn `j > i` und `1 < j < ilo` oder `j > ihi`. `scale` enthält Informationen über die durchgeführten Skalierungen/Permutation.
