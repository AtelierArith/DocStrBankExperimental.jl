```
QRPivoted <: Factorization
```

Une factorisation matricielle QR avec pivotement de colonnes dans un format compact, généralement obtenue à partir de [`qr`](@ref). Si $A$ est une matrice `m`×`n`, alors

$$
A P = Q R
$$

où $P$ est une matrice de permutation, $Q$ est une matrice orthogonale/unitaire et $R$ est triangulaire supérieure. La matrice $Q$ est stockée sous forme d'une séquence de réflecteurs de Householder :

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T).
$$

L'itération de la décomposition produit les composants `Q`, `R` et `p`.

L'objet a trois champs :

  * `factors` est une matrice `m`×`n`.

      * La partie triangulaire supérieure contient les éléments de $R$, c'est-à-dire `R = triu(F.factors)` pour un objet `QR` `F`.
      * La partie sous-diagonale contient les réflecteurs $v_i$ stockés dans un format compact où $v_i$ est la $i$-ème colonne de la matrice `V = I + tril(F.factors, -1)`.
  * `τ` est un vecteur de longueur `min(m,n)` contenant les coefficients $au_i$.
  * `jpvt` est un vecteur entier de longueur `n` correspondant à la permutation $P$.
