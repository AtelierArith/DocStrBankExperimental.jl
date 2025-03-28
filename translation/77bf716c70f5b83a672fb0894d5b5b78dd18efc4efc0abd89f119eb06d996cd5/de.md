```
asin(A::AbstractMatrix)
```

Berechne den inversen Matrixsinus einer quadratischen Matrix `A`.

Wenn `A` symmetrisch oder hermitesch ist, wird ihre Eigenzerlegung ([`eigen`](@ref)) verwendet, um den inversen Sinus zu berechnen. Andernfalls wird der inverse Sinus unter Verwendung von [`log`](@ref) und [`sqrt`](@ref) bestimmt. Für die Theorie und die logarithmischen Formeln, die zur Berechnung dieser Funktion verwendet werden, siehe [^AH16_2].

[^AH16_2]: Mary Aprahamian und Nicholas J. Higham, "Matrix Inverse Trigonometric and Inverse Hyperbolic Functions: Theory and Algorithms", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# Beispiele

```julia-repl
julia> asin(sin([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5-4.16334e-17im  0.1-5.55112e-17im
 -0.2+9.71445e-17im  0.3-1.249e-16im
```
