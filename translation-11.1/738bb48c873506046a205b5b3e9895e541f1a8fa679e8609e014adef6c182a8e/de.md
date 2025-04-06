```
QRPivoted <: Factorization
```

Eine QR-Matrixfaktorisierung mit Spaltenpivotierung in einem kompakten Format, typischerweise erhalten von [`qr`](@ref). Wenn $A$ eine `m`×`n` Matrix ist, dann

$$
A P = Q R
$$

wobei $P$ eine Permutationsmatrix ist, $Q$ eine orthogonale/einheitliche Matrix und $R$ oberhalb dreieckig ist. Die Matrix $Q$ wird als eine Folge von Householder-Reflektoren gespeichert:

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T).
$$

Das Iterieren der Zerlegung produziert die Komponenten `Q`, `R` und `p`.

Das Objekt hat drei Felder:

  * `factors` ist eine `m`×`n` Matrix.

      * Der obere dreieckige Teil enthält die Elemente von $R$, das heißt `R = triu(F.factors)` für ein `QR` Objekt `F`.
      * Der subdiagonale Teil enthält die Reflektoren $v_i$, die in einem kompakten Format gespeichert sind, wobei $v_i$ die $i$-te Spalte der Matrix `V = I + tril(F.factors, -1)` ist.
  * `τ` ist ein Vektor der Länge `min(m,n)`, der die Koeffizienten $au_i$ enthält.
  * `jpvt` ist ein ganzzahliger Vektor der Länge `n`, der der Permutation $P$ entspricht.
