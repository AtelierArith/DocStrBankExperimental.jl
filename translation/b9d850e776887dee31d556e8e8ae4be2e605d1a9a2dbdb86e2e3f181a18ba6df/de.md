```
QRCompactWY <: Factorization
```

Eine QR-Matrixfaktorisierung, die in einem kompakten Blockformat gespeichert ist, typischerweise erhalten von [`qr`](@ref). Wenn $A$ eine `m`×`n` Matrix ist, dann

$$
A = Q R
$$

wobei $Q$ eine orthogonale/einheitliche Matrix und $R$ oberes Dreieck ist. Es ist ähnlich zum [`QR`](@ref) Format, mit dem Unterschied, dass die orthogonale/einheitliche Matrix $Q$ im *Compact WY* Format gespeichert ist [^Schreiber1989]. Für die Blockgröße $n_b$ wird es als eine `m`×`n` untere trapezförmige Matrix $V$ und eine Matrix $T = (T_1 \; T_2 \; ... \; T_{b-1} \; T_b')$ gespeichert, die aus $b = \lceil \min(m,n) / n_b \rceil$ oberen Dreiecksmatrizen $T_j$ der Größe $n_b$×$n_b$ ($j = 1, ..., b-1$) und einer oberen trapezförmigen $n_b$×$\min(m,n) - (b-1) n_b$ Matrix $T_b'$ ($j=b$) besteht, deren oberer quadratischer Teil mit $T_b$ bezeichnet wird und die erfüllt

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T)
= \prod_{j=1}^{b} (I - V_j T_j V_j^T)
$$

so dass $v_i$ die $i$-te Spalte von $V$ ist, $\tau_i$ das $i$-te Element von `[diag(T_1); diag(T_2); …; diag(T_b)]` ist, und $(V_1 \; V_2 \; ... \; V_b)$ der linke `m`×`min(m, n)` Block von $V$ ist. Wenn es mit [`qr`](@ref) konstruiert wird, wird die Blockgröße durch $n_b = \min(m, n, 36)$ gegeben.

Das Iterieren der Zerlegung erzeugt die Komponenten `Q` und `R`.

Das Objekt hat zwei Felder:

  * `factors`, wie im [`QR`](@ref) Typ, ist eine `m`×`n` Matrix.

      * Der obere Dreiecksteil enthält die Elemente von $R$, das heißt `R = triu(F.factors)` für ein `QR` Objekt `F`.
      * Der subdiagonale Teil enthält die Reflektoren $v_i$, die in einem gepackten Format gespeichert sind, so dass `V = I + tril(F.factors, -1)`.
  * `T` ist eine $n_b$-by-$\min(m,n)$ Matrix, wie oben beschrieben. Die subdiagonalen Elemente für jede Dreiecksmatrix $T_j$ werden ignoriert.

!!! note
    Dieses Format sollte nicht mit der älteren *WY* Darstellung [^Bischof1987] verwechselt werden.


[^Bischof1987]: C Bischof und C Van Loan, "Die WY-Darstellung für Produkte von Householder-Matrizen", SIAM J Sci Stat Comput 8 (1987), s2-s13. [doi:10.1137/0908009](https://doi.org/10.1137/0908009)

[^Schreiber1989]: R Schreiber und C Van Loan, "Eine speichereffiziente WY-Darstellung für Produkte von Householder-Transformationen", SIAM J Sci Stat Comput 10 (1989), 53-57. [doi:10.1137/0910005](https://doi.org/10.1137/0910005)
