```
ordschur(F::Schur, select::Union{Vector{Bool},BitVector}) -> F::Schur
```

Réorganise la factorisation de Schur `F` d'une matrice `A = Z*T*Z'` selon le tableau logique `select`, retournant l'objet de factorisation réordonné `F`. Les valeurs propres sélectionnées apparaissent dans la diagonale principale de `F.Schur` et les colonnes principales correspondantes de `F.vectors` forment une base orthogonale/unitaire du sous-espace invariant à droite correspondant. Dans le cas réel, une paire de valeurs propres conjuguées complexes doit être soit entièrement incluse, soit entièrement exclue via `select`.
