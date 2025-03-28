```
trexc!(compq, ifst, ilst, T, Q) -> (T, Q)
trexc!(ifst, ilst, T, Q) -> (T, Q)
```

Réorganiser la factorisation de Schur `T` d'une matrice, de sorte que le bloc diagonal de `T` avec l'indice de ligne `ifst` soit déplacé à l'indice de ligne `ilst`. Si `compq = V`, les vecteurs de Schur `Q` sont réordonnés. Si `compq = N`, ils ne sont pas modifiés. La méthode à 4 arguments appelle la méthode à 5 arguments avec `compq = V`.
