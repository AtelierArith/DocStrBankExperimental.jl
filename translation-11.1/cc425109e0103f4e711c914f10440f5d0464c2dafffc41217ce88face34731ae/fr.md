```
condskeel(M, [x, p::Real=Inf])
```

$$
\kappa_S(M, p) = \left\Vert \left\vert M \right\vert \left\vert M^{-1} \right\vert \right\Vert_p \\
\kappa_S(M, x, p) = \frac{\left\Vert \left\vert M \right\vert \left\vert M^{-1} \right\vert \left\vert x \right\vert \right\Vert_p}{\left \Vert x \right \Vert_p}
$$

Le nombre de condition de Skeel $\kappa_S$ de la matrice `M`, éventuellement par rapport au vecteur `x`, est calculé en utilisant la norme opérateur `p`. $\left\vert M \right\vert$ désigne la matrice des valeurs absolues (élément par élément) de $M$; $\left\vert M \right\vert_{ij} = \left\vert M_{ij} \right\vert$. Les valeurs valides pour `p` sont `1`, `2` et `Inf` (par défaut).

Cette quantité est également connue dans la littérature sous le nom de nombre de condition de Bauer, nombre de condition relatif, ou nombre de condition relatif élément par élément.
