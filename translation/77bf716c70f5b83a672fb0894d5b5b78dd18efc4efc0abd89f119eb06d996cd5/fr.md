```
asin(A::AbstractMatrix)
```

Calculez le sinus inverse de matrice d'une matrice carrée `A`.

Si `A` est symétrique ou hermitienne, sa décomposition en valeurs propres ([`eigen`](@ref)) est utilisée pour calculer le sinus inverse. Sinon, le sinus inverse est déterminé en utilisant [`log`](@ref) et [`sqrt`](@ref). Pour la théorie et les formules logarithmiques utilisées pour calculer cette fonction, voir [^AH16_2].

[^AH16_2]: Mary Aprahamian et Nicholas J. Higham, "Matrix Inverse Trigonometric and Inverse Hyperbolic Functions: Theory and Algorithms", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# Exemples

```julia-repl
julia> asin(sin([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5-4.16334e-17im  0.1-5.55112e-17im
 -0.2+9.71445e-17im  0.3-1.249e-16im
```
