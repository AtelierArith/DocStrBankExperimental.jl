```
ordschur(F::GeneralizedSchur, select::Union{Vector{Bool},BitVector}) -> F::GeneralizedSchur
```

Réorganise la factorisation de Schur généralisée `F` d'une paire de matrices `(A, B) = (Q*S*Z', Q*T*Z')` selon le tableau logique `select` et renvoie un objet GeneralizedSchur `F`. Les valeurs propres sélectionnées apparaissent dans la diagonale principale de `F.S` et `F.T`, et les vecteurs de Schur orthogonaux/unitaires à gauche et à droite sont également réorganisés de sorte que `(A, B) = F.Q*(F.S, F.T)*F.Z'` reste valide et que les valeurs propres généralisées de `A` et `B` puissent toujours être obtenues avec `F.α./F.β`.
