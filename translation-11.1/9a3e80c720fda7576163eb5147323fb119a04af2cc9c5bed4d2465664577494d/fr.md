```
eps(x::AbstractFloat)
```

Retourne l'*unité dans la dernière place* (ulp) de `x`. C'est la distance entre les valeurs flottantes représentables consécutives à `x`. Dans la plupart des cas, si la distance de chaque côté de `x` est différente, alors la plus grande des deux est prise, c'est-à-dire

```
eps(x) == max(x-prevfloat(x), nextfloat(x)-x)
```

Les exceptions à cette règle sont les plus petites et les plus grandes valeurs finies (par exemple, `nextfloat(-Inf)` et `prevfloat(Inf)` pour [`Float64`](@ref)), qui arrondissent à la plus petite des valeurs.

La raison de ce comportement est que `eps` borne l'erreur d'arrondi en virgule flottante. Sous le mode d'arrondi par défaut `RoundNearest`, si $y$ est un nombre réel et $x$ est le nombre en virgule flottante le plus proche de $y$, alors

$$
|y-x| \leq \operatorname{eps}(x)/2.
$$

Voir aussi : [`nextfloat`](@ref), [`issubnormal`](@ref), [`floatmax`](@ref).

# Exemples

```jldoctest
julia> eps(1.0)
2.220446049250313e-16

julia> eps(prevfloat(2.0))
2.220446049250313e-16

julia> eps(2.0)
4.440892098500626e-16

julia> x = prevfloat(Inf)      # plus grand Float64 fini
1.7976931348623157e308

julia> x + eps(x)/2            # arrondit vers le haut
Inf

julia> x + prevfloat(eps(x)/2) # arrondit vers le bas
1.7976931348623157e308
```
