```
GeneralizedSchur <: Factorization
```

Type de factorisation matricielle de la factorisation de Schur généralisée de deux matrices `A` et `B`. C'est le type de retour de [`schur(_, _)`](@ref), la fonction de factorisation matricielle correspondante.

Si `F::GeneralizedSchur` est l'objet de factorisation, les facteurs de Schur (quasi) triangulaires peuvent être obtenus via `F.S` et `F.T`, les vecteurs de Schur unitaires/orthogonaux à gauche via `F.left` ou `F.Q`, et les vecteurs de Schur unitaires/orthogonaux à droite peuvent être obtenus avec `F.right` ou `F.Z` de sorte que `A=F.left*F.S*F.right'` et `B=F.left*F.T*F.right'`. Les valeurs propres généralisées de `A` et `B` peuvent être obtenues avec `F.α./F.β`.

L'itération de la décomposition produit les composants `F.S`, `F.T`, `F.Q`, `F.Z`, `F.α`, et `F.β`.
