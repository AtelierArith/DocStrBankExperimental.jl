```
condskeel(M, [x, p::Real=Inf])
```

$$
\kappa_S(M, p) = \left\Vert \left\vert M \right\vert \left\vert M^{-1} \right\vert \right\Vert_p \\
\kappa_S(M, x, p) = \frac{\left\Vert \left\vert M \right\vert \left\vert M^{-1} \right\vert \left\vert x \right\vert \right\Vert_p}{\left \Vert x \right \Vert_p}
$$

Skeel-Bedingungszahl $\kappa_S$ der Matrix `M`, optional in Bezug auf den Vektor `x`, wie mit der Operator `p`-Norm berechnet. $\left\vert M \right\vert$ bezeichnet die Matrix der (einträgeweise) absoluten Werte von $M$; $\left\vert M \right\vert_{ij} = \left\vert M_{ij} \right\vert$. Gültige Werte für `p` sind `1`, `2` und `Inf` (Standard).

Diese Größe ist auch in der Literatur als Bauer-Bedingungszahl, relative Bedingungszahl oder komponentenweise relative Bedingungszahl bekannt.
