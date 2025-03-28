```
logrange(début, fin, longueur)
logrange(début, fin; longueur)
```

Construit un tableau spécialisé dont les éléments sont espacés logarithmiquement entre les points de départ et d'arrivée donnés. C'est-à-dire que le rapport des éléments successifs est constant, calculé à partir de la longueur.

C'est similaire à `geomspace` en Python. Contrairement à `PowerRange` dans Mathematica, vous spécifiez le nombre d'éléments et non le rapport. Contrairement à `logspace` en Python et Matlab, les arguments `début` et `fin` sont toujours les premier et dernier éléments du résultat, et non des puissances appliquées à une certaine base.

# Exemples

```jldoctest
julia> logrange(10, 4000, longueur=3)
3-élément Base.LogRange{Float64, Base.TwicePrecision{Float64}}:
 10.0, 200.0, 4000.0

julia> ans[2] ≈ sqrt(10 * 4000)  # l'élément du milieu est la moyenne géométrique
true

julia> range(10, 40, longueur=3)[2] ≈ (10 + 40)/2  # moyenne arithmétique
true

julia> logrange(1f0, 32f0, 11)
11-élément Base.LogRange{Float32, Float64}:
 1.0, 1.41421, 2.0, 2.82843, 4.0, 5.65685, 8.0, 11.3137, 16.0, 22.6274, 32.0

julia> logrange(1, 1000, longueur=4) ≈ 10 .^ (0:3)
true
```

Voir le type [`LogRange`](@ref Base.LogRange) pour plus de détails.

Voir aussi [`range`](@ref) pour des points espacés linéairement.

!!! compat "Julia 1.11"
    Cette fonction nécessite au moins Julia 1.11.

