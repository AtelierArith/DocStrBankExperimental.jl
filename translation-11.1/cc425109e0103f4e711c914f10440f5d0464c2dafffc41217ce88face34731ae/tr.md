```
condskeel(M, [x, p::Gerçek=Inf])
```

$$
\kappa_S(M, p) = \left\Vert \left\vert M \right\vert \left\vert M^{-1} \right\vert \right\Vert_p \\
\kappa_S(M, x, p) = \frac{\left\Vert \left\vert M \right\vert \left\vert M^{-1} \right\vert \left\vert x \right\vert \right\Vert_p}{\left \Vert x \right \Vert_p}
$$

Matris `M`'nin Skeel koşul sayısı $\kappa_S$, isteğe bağlı olarak `x` vektörüne göre, `p`-norm operatörü kullanılarak hesaplanır. $\left\vert M \right\vert$, $M$'nin (eleman bazında) mutlak değerler matrisini ifade eder; $\left\vert M \right\vert_{ij} = \left\vert M_{ij} \right\vert$. `p` için geçerli değerler `1`, `2` ve `Inf`'dir (varsayılan).

Bu miktar, literatürde Bauer koşul sayısı, göreceli koşul sayısı veya bileşen bazında göreceli koşul sayısı olarak da bilinir.
