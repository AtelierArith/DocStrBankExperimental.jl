```
SparseArrays.sparse!(I, J, V, [m, n, combine]) -> SparseMatrixCSC
```

Variante de `sparse!` qui réutilise les vecteurs d'entrée (`I`, `J`, `V`) pour le stockage final de la matrice. Après construction, les vecteurs d'entrée aliaseront les tampons de la matrice ; `S.colptr === I`, `S.rowval === J`, et `S.nzval === V` est vrai, et ils seront redimensionnés si nécessaire.

Notez que certains tampons de travail seront toujours alloués. En particulier, cette méthode est un wrapper de commodité autour de `sparse!(I, J, V, m, n, combine, klasttouch, csrrowptr, csrcolval, csrnzval, csccolptr, cscrowval, cscnzval)` où cette méthode alloue `klasttouch`, `csrrowptr`, `csrcolval`, et `csrnzval` de taille appropriée, mais réutilise `I`, `J`, et `V` pour `csccolptr`, `cscrowval`, et `cscnzval`.

Les arguments `m`, `n`, et `combine` par défaut à `maximum(I)`, `maximum(J)`, et `+`, respectivement.

!!! compat "Julia 1.10"
    Cette méthode nécessite la version Julia 1.10 ou ultérieure.

