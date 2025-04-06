```
atan(A::AbstractMatrix)
```

Berechne den inversen Matrixtangens einer quadratischen Matrix `A`.

Wenn `A` symmetrisch oder hermitesch ist, wird ihre Eigenzerlegung ([`eigen`](@ref)) verwendet, um den inversen Tangens zu berechnen. Andernfalls wird der inverse Tangens unter Verwendung von [`log`](@ref) bestimmt. Für die Theorie und die logarithmischen Formeln, die zur Berechnung dieser Funktion verwendet werden, siehe [^AH16_3].

[^AH16_3]: Mary Aprahamian und Nicholas J. Higham, "Matrix Inverse Trigonometric and Inverse Hyperbolic Functions: Theory and Algorithms", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# Beispiele

```julia-repl
julia> atan(tan([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5+1.38778e-17im  0.1-2.77556e-17im
 -0.2+6.93889e-17im  0.3-4.16334e-17im
```
