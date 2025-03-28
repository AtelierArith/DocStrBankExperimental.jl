```
QR <: Factorization
```

Une factorisation matricielle QR stockée dans un format compact, généralement obtenue à partir de [`qr`](@ref). Si $A$ est une matrice `m`×`n`, alors

$$
A = Q R
$$

où $Q$ est une matrice orthogonale/unitaire et $R$ est triangulaire supérieure. La matrice $Q$ est stockée sous la forme d'une séquence de réflecteurs de Householder $v_i$ et de coefficients $\tau_i$ où :

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T).
$$

L'itération de la décomposition produit les composants `Q` et `R`.

L'objet a deux champs :

  * `factors` est une matrice `m`×`n`.

      * La partie triangulaire supérieure contient les éléments de $R$, c'est-à-dire `R = triu(F.factors)` pour un objet `QR` `F`.
      * La partie subdiagonale contient les réflecteurs $v_i$ stockés dans un format compact où $v_i$ est la $i$-ème colonne de la matrice `V = I + tril(F.factors, -1)`.
  * `τ` est un vecteur de longueur `min(m,n)` contenant les coefficients $au_i$.
