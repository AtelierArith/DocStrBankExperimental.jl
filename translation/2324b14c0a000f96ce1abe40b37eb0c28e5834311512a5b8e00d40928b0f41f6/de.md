```
QR <: Faktorisierung
```

Eine QR-Matrixfaktorisierung, die in einem kompakten Format gespeichert ist, typischerweise erhalten von [`qr`](@ref). Wenn $A$ eine `m`×`n` Matrix ist, dann

$$
A = Q R
$$

wobei $Q$ eine orthogonale/einheitliche Matrix und $R$ oberes Dreieck ist. Die Matrix $Q$ wird als eine Folge von Householder-Reflektoren $v_i$ und Koeffizienten $\tau_i$ gespeichert, wobei:

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T).
$$

Das Iterieren der Zerlegung erzeugt die Komponenten `Q` und `R`.

Das Objekt hat zwei Felder:

  * `factors` ist eine `m`×`n` Matrix.

      * Der obere Dreiecksteil enthält die Elemente von $R$, das heißt `R = triu(F.factors)` für ein `QR` Objekt `F`.
      * Der subdiagonale Teil enthält die Reflektoren $v_i$, die in einem kompakten Format gespeichert sind, wobei $v_i$ die $i$-te Spalte der Matrix `V = I + tril(F.factors, -1)` ist.
  * `τ` ist ein Vektor der Länge `min(m,n)`, der die Koeffizienten $au_i$ enthält.
