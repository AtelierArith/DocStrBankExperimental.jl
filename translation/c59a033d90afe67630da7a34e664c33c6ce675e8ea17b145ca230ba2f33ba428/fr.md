```
schur(A, B) -> F::GeneralizedSchur
```

Calcule la factorisation de Schur généralisée (ou QZ) des matrices `A` et `B`. Les facteurs de Schur (quasi) triangulaires peuvent être obtenus à partir de l'objet `Schur` `F` avec `F.S` et `F.T`, les vecteurs de Schur unitaires/orthogonaux à gauche peuvent être obtenus avec `F.left` ou `F.Q` et les vecteurs de Schur unitaires/orthogonaux à droite peuvent être obtenus avec `F.right` ou `F.Z` de sorte que `A=F.left*F.S*F.right'` et `B=F.left*F.T*F.right'`. Les valeurs propres généralisées de `A` et `B` peuvent être obtenues avec `F.α./F.β`.

L'itération de la décomposition produit les composants `F.S`, `F.T`, `F.Q`, `F.Z`, `F.α` et `F.β`.
