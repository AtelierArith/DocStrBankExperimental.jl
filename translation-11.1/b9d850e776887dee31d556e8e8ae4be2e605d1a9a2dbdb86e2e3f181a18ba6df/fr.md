```
QRCompactWY <: Factorization
```

Une factorisation matricielle QR stockée dans un format compact bloqué, généralement obtenue à partir de [`qr`](@ref). Si $A$ est une matrice `m`×`n`, alors

$$
A = Q R
$$

où $Q$ est une matrice orthogonale/unitaire et $R$ est triangulaire supérieure. C'est similaire au format [`QR`](@ref) sauf que la matrice orthogonale/unitaire $Q$ est stockée au format *Compact WY* [^Schreiber1989]. Pour la taille de bloc $n_b$, elle est stockée sous la forme d'une matrice trapézoïdale inférieure `m`×`n` $V$ et d'une matrice $T = (T_1 \; T_2 \; ... \; T_{b-1} \; T_b')$ composée de $b = \lceil \min(m,n) / n_b \rceil$ matrices triangulaires supérieures $T_j$ de taille $n_b$×$n_b$ ($j = 1, ..., b-1$) et d'une matrice trapézoïdale supérieure $n_b$×$\min(m,n) - (b-1) n_b$ $T_b'$ ($j=b$) dont la partie carrée supérieure est notée avec $T_b$ satisfaisant

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T)
= \prod_{j=1}^{b} (I - V_j T_j V_j^T)
$$

tel que $v_i$ est la $i$-ème colonne de $V$, $\tau_i$ est le $i$-ème élément de `[diag(T_1); diag(T_2); …; diag(T_b)]`, et $(V_1 \; V_2 \; ... \; V_b)$ est le bloc gauche `m`×`min(m, n)` de $V$. Lorsqu'il est construit à l'aide de [`qr`](@ref), la taille de bloc est donnée par $n_b = \min(m, n, 36)$.

L'itération de la décomposition produit les composants `Q` et `R`.

L'objet a deux champs :

  * `factors`, comme dans le type [`QR`](@ref), est une matrice `m`×`n`.

      * La partie triangulaire supérieure contient les éléments de $R$, c'est-à-dire `R = triu(F.factors)` pour un objet `QR` `F`.
      * La partie subdiagonale contient les réflecteurs $v_i$ stockés dans un format compact tel que `V = I + tril(F.factors, -1)`.
  * `T` est une matrice $n_b$-par-$\min(m,n)$ comme décrit ci-dessus. Les éléments subdiagonaux pour chaque matrice triangulaire $T_j$ sont ignorés.

!!! note
    Ce format ne doit pas être confondu avec l'ancienne représentation *WY* [^Bischof1987].


[^Bischof1987]: C Bischof et C Van Loan, "La représentation WY pour les produits de matrices de Householder", SIAM J Sci Stat Comput 8 (1987), s2-s13. [doi:10.1137/0908009](https://doi.org/10.1137/0908009)

[^Schreiber1989]: R Schreiber et C Van Loan, "Une représentation WY efficace en termes de stockage pour les produits de transformations de Householder", SIAM J Sci Stat Comput 10 (1989), 53-57. [doi:10.1137/0910005](https://doi.org/10.1137/0910005)
