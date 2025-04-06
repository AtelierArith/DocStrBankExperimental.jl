```
SparseArrays.spzeros!(::Type{Tv}, I, J, [m, n]) -> SparseMatrixCSC{Tv}
```

Variante de `spzeros!` qui réutilise les vecteurs d'entrée `I` et `J` pour le stockage de la matrice finale. Après construction, les vecteurs d'entrée aliaseront les tampons de la matrice ; `S.colptr === I` et `S.rowval === J` est vrai, et ils seront redimensionnés si nécessaire.

Notez que certains tampons de travail seront toujours alloués. En particulier, cette méthode est un wrapper de commodité autour de `spzeros!(Tv, I, J, m, n, klasttouch, csrrowptr, csrcolval, csccolptr, cscrowval)` où cette méthode alloue `klasttouch`, `csrrowptr`, et `csrcolval` de taille appropriée, mais réutilise `I` et `J` pour `csccolptr` et `cscrowval`.

Les arguments `m` et `n` par défaut à `maximum(I)` et `maximum(J)`.

!!! compat "Julia 1.10"
    Cette méthode nécessite la version Julia 1.10 ou ultérieure.

