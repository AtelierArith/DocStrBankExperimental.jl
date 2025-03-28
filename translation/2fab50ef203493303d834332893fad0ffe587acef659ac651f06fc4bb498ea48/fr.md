```
lowrankdowndate!(C::Cholesky, v::AbstractVector) -> CC::Cholesky
```

Met à jour une factorisation de Cholesky `C` avec le vecteur `v`. Si `A = C.U'C.U` alors `CC = cholesky(C.U'C.U - v*v')` mais le calcul de `CC` n'utilise que `O(n^2)` opérations. La factorisation d'entrée `C` est mise à jour sur place de sorte qu'à la sortie `C == CC`. Le vecteur `v` est détruit pendant le calcul.
