```
acos(A::AbstractMatrix)
```

Calcule le cosinus inverse d'une matrice carrée `A`.

Si `A` est symétrique ou hermitienne, sa décomposition en valeurs propres ([`eigen`](@ref)) est utilisée pour calculer le cosinus inverse. Sinon, le cosinus inverse est déterminé en utilisant [`log`](@ref) et [`sqrt`](@ref). Pour la théorie et les formules logarithmiques utilisées pour calculer cette fonction, voir [^AH16_1].

[^AH16_1]: Mary Aprahamian et Nicholas J. Higham, "Fonctions trigonométriques inverses de matrice et fonctions hyperboliques inverses : théorie et algorithmes", MIMS EPrint : 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# Exemples

```julia-repl
julia> acos(cos([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5-8.32667e-17im  0.1+0.0im
 -0.2+2.63678e-16im  0.3-3.46945e-16im
```
