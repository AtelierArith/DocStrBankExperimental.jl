```
QRPivoted <: Factorization
```

Una factorización de matriz QR con pivoteo de columnas en un formato empaquetado, típicamente obtenida de [`qr`](@ref). Si $A$ es una matriz `m`×`n`, entonces

$$
A P = Q R
$$

donde $P$ es una matriz de permutación, $Q$ es una matriz ortogonal/unitaria y $R$ es triangular superior. La matriz $Q$ se almacena como una secuencia de reflectores de Householder:

$$
Q = \prod_{i=1}^{\min(m,n)} (I - \tau_i v_i v_i^T).
$$

Iterar la descomposición produce los componentes `Q`, `R` y `p`.

El objeto tiene tres campos:

  * `factors` es una matriz `m`×`n`.

      * La parte triangular superior contiene los elementos de $R$, es decir, `R = triu(F.factors)` para un objeto `QR` `F`.
      * La parte subdiagonal contiene los reflectores $v_i$ almacenados en un formato empaquetado donde $v_i$ es la $i$-ésima columna de la matriz `V = I + tril(F.factors, -1)`.
  * `τ` es un vector de longitud `min(m,n)` que contiene los coeficientes $au_i$.
  * `jpvt` es un vector entero de longitud `n` correspondiente a la permutación $P$.
