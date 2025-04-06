```
QRCompactWY <: Factorization
```

Una factorización de matriz QR almacenada en un formato compacto bloqueado, típicamente obtenida de [`qr`](@ref). Si $A$ es una matriz `m`×`n`, entonces

$$
A = Q R
$$

donde $Q$ es una matriz ortogonal/unitaria y $R$ es triangular superior. Es similar al formato [`QR`](@ref) excepto que la matriz ortogonal/unitaria $Q$ se almacena en formato *Compact WY* [^Schreiber1989]. Para el tamaño de bloque $n_b$, se almacena como una matriz trapezoidal inferior `m`×`n` $V$ y una matriz $T = (T_1 \; T_2 \; ... \; T_{b-1} \; T_b')$ compuesta de $b = \lceil \min(m,n) / n_b \rceil$ matrices triangulares superiores $T_j$ de tamaño $n_b$×$n_b$ ($j = 1, ..., b-1$) y una matriz trapezoidal superior $n_b$×$\min(m,n) - (b-1) n_b$ $T_b'$ ($j=b$) cuya parte cuadrada superior se denota con $T_b$ satisfaciendo

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T)
= \prod_{j=1}^{b} (I - V_j T_j V_j^T)
$$

de modo que $v_i$ es la $i$-ésima columna de $V$, $\tau_i$ es el $i$-ésimo elemento de `[diag(T_1); diag(T_2); …; diag(T_b)]`, y $(V_1 \; V_2 \; ... \; V_b)$ es el bloque izquierdo `m`×`min(m, n)` de $V$. Cuando se construye utilizando [`qr`](@ref), el tamaño del bloque está dado por $n_b = \min(m, n, 36)$.

Iterar la descomposición produce los componentes `Q` y `R`.

El objeto tiene dos campos:

  * `factors`, como en el tipo [`QR`](@ref), es una matriz `m`×`n`.

      * La parte triangular superior contiene los elementos de $R$, es decir, `R = triu(F.factors)` para un objeto `QR` `F`.
      * La parte subdiagonal contiene los reflectores $v_i$ almacenados en un formato empaquetado tal que `V = I + tril(F.factors, -1)`.
  * `T` es una matriz de $n_b$ por $\min(m,n)$ como se describió anteriormente. Se ignoran los elementos subdiagonales para cada matriz triangular $T_j$.

!!! note
    Este formato no debe confundirse con la representación *WY* más antigua [^Bischof1987].


[^Bischof1987]: C Bischof y C Van Loan, "La representación WY para productos de matrices de Householder", SIAM J Sci Stat Comput 8 (1987), s2-s13. [doi:10.1137/0908009](https://doi.org/10.1137/0908009)

[^Schreiber1989]: R Schreiber y C Van Loan, "Una representación WY eficiente en almacenamiento para productos de transformaciones de Householder", SIAM J Sci Stat Comput 10 (1989), 53-57. [doi:10.1137/0910005](https://doi.org/10.1137/0910005)
