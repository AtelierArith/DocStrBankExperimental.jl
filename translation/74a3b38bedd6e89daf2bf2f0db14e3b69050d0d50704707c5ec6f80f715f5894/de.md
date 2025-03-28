```
log(A::AbstractMatrix)
```

Wenn `A` keinen negativen reellen Eigenwert hat, berechne den Hauptmatrixlogarithmus von `A`, d.h. die eindeutige Matrix $X$, so dass $e^X = A$ und $-\pi < Im(\lambda) < \pi$ für alle Eigenwerte $\lambda$ von $X$. Wenn `A` nichtpositive Eigenwerte hat, wird wann immer möglich eine nicht-hauptsächliche Matrixfunktion zurückgegeben.

Wenn `A` symmetrisch oder hermitesch ist, wird die Eigenzerlegung ([`eigen`](@ref)) verwendet, wenn `A` dreieckig ist, wird eine verbesserte Version der inversen Skalierungs- und Quadraturmethode angewendet (siehe [^AH12] und [^AHR13]). Wenn `A` reell ist und keine negativen Eigenwerte hat, wird die reelle Schur-Form berechnet. Andernfalls wird die komplexe Schur-Form berechnet. Dann wird der obere (quasi-)dreieckige Algorithmus in [^AHR13] auf den oberen (quasi-)dreieckigen Faktor angewendet.

[^AH12]: Awad H. Al-Mohy und Nicholas J. Higham, "Verbesserte inverse Skalierungs- und Quadraturalgorithmen für den Matrixlogarithmus", SIAM Journal on Scientific Computing, 34(4), 2012, C153-C169. [doi:10.1137/110852553](https://doi.org/10.1137/110852553)

[^AHR13]: Awad H. Al-Mohy, Nicholas J. Higham und Samuel D. Relton, "Berechnung der Fréchet-Ableitung des Matrixlogarithmus und Schätzung der Konditionszahl", SIAM Journal on Scientific Computing, 35(4), 2013, C394-C410. [doi:10.1137/120885991](https://doi.org/10.1137/120885991)

# Beispiele

```jldoctest
julia> A = Matrix(2.7182818*I, 2, 2)
2×2 Matrix{Float64}:
 2.71828  0.0
 0.0      2.71828

julia> log(A)
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
