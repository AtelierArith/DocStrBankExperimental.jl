```
condskeel(M, [x, p::Real=Inf])
```

$$
\kappa_S(M, p) = \left\Vert \left\vert M \right\vert \left\vert M^{-1} \right\vert \right\Vert_p \\
\kappa_S(M, x, p) = \frac{\left\Vert \left\vert M \right\vert \left\vert M^{-1} \right\vert \left\vert x \right\vert \right\Vert_p}{\left \Vert x \right \Vert_p}
$$

El número de condición de Skeel $\kappa_S$ de la matriz `M`, opcionalmente con respecto al vector `x`, se calcula utilizando la norma del operador `p`. $\left\vert M \right\vert$ denota la matriz de valores absolutos (por entrada) de $M$; $\left\vert M \right\vert_{ij} = \left\vert M_{ij} \right\vert$. Los valores válidos para `p` son `1`, `2` e `Inf` (por defecto).

Esta cantidad también se conoce en la literatura como el número de condición de Bauer, número de condición relativo o número de condición relativo por componente.
