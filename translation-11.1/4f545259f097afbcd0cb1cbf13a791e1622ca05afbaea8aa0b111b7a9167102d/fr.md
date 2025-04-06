```
atan(A::AbstractMatrix)
```

Calcule la tangente inverse de matrice d'une matrice carrée `A`.

Si `A` est symétrique ou hermitienne, son eigendecomposition ([`eigen`](@ref)) est utilisée pour calculer la tangente inverse. Sinon, la tangente inverse est déterminée en utilisant [`log`](@ref). Pour la théorie et les formules logarithmiques utilisées pour calculer cette fonction, voir [^AH16_3].

[^AH16_3]: Mary Aprahamian et Nicholas J. Higham, "Fonctions trigonométriques inverses de matrice et fonctions hyperboliques inverses : théorie et algorithmes", MIMS EPrint : 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# Exemples

```julia-repl
julia> atan(tan([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5+1.38778e-17im  0.1-2.77556e-17im
 -0.2+6.93889e-17im  0.3-4.16334e-17im
```
