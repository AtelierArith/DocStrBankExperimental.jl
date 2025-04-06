```
log(A::AbstractMatrix)
```

Si `A` n'a pas de valeur propre réelle négative, calculez le logarithme matriciel principal de `A`, c'est-à-dire la matrice unique $X$ telle que $e^X = A$ et $-\pi < Im(\lambda) < \pi$ pour toutes les valeurs propres $\lambda$ de $X$. Si `A` a des valeurs propres non positives, une fonction matricielle non principale est renvoyée chaque fois que cela est possible.

Si `A` est symétrique ou hermitienne, sa décomposition en valeurs propres ([`eigen`](@ref)) est utilisée, si `A` est triangulaire, une version améliorée de la méthode d'inversion par mise à l'échelle et de mise à l'échelle est employée (voir [^AH12] et [^AHR13]). Si `A` est réel sans valeurs propres négatives, alors la forme de Schur réelle est calculée. Sinon, la forme de Schur complexe est calculée. Ensuite, l'algorithme triangulaire supérieur (quasi-)triangulaire dans [^AHR13] est utilisé sur le facteur supérieur (quasi-)triangulaire.

[^AH12]: Awad H. Al-Mohy et Nicholas J. Higham, "Amélioration des algorithmes d'inversion par mise à l'échelle et de mise à l'échelle pour le logarithme matriciel", SIAM Journal on Scientific Computing, 34(4), 2012, C153-C169. [doi:10.1137/110852553](https://doi.org/10.1137/110852553)

[^AHR13]: Awad H. Al-Mohy, Nicholas J. Higham et Samuel D. Relton, "Calcul du dérivé de Fréchet du logarithme matriciel et estimation du nombre de condition", SIAM Journal on Scientific Computing, 35(4), 2013, C394-C410. [doi:10.1137/120885991](https://doi.org/10.1137/120885991)

# Exemples

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
