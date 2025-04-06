```
@evalpoly(z, c...)
```

Évalue le polynôme $\sum_k z^{k-1} c[k]$ pour les coefficients `c[1]`, `c[2]`, ...; c'est-à-dire que les coefficients sont donnés dans l'ordre croissant par puissance de `z`. Cette macro se développe en un code en ligne efficace qui utilise soit la méthode de Horner, soit, pour des `z` complexes, un algorithme plus efficace de type Goertzel.

Voir aussi [`evalpoly`](@ref).

# Exemples

```jldoctest
julia> @evalpoly(3, 1, 0, 1)
10

julia> @evalpoly(2, 1, 0, 1)
5

julia> @evalpoly(2, 1, 1, 1)
7
```
