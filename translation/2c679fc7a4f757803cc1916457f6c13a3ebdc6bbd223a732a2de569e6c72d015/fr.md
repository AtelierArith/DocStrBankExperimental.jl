```
deleteat!(a::Vector, inds)
```

Supprime les éléments aux indices donnés par `inds`, et retourne le `a` modifié. Les éléments suivants sont décalés pour combler le vide résultant.

`inds` peut être soit un itérateur, soit une collection d'indices entiers triés et uniques, ou un vecteur booléen de la même longueur que `a` avec `true` indiquant les entrées à supprimer.

# Exemples

```jldoctest
julia> deleteat!([6, 5, 4, 3, 2, 1], 1:2:5)
3-element Vector{Int64}:
 5
 3
 1

julia> deleteat!([6, 5, 4, 3, 2, 1], [true, false, true, false, true, false])
3-element Vector{Int64}:
 5
 3
 1

julia> deleteat!([6, 5, 4, 3, 2, 1], (2, 2))
ERROR: ArgumentError: indices must be unique and sorted
Stacktrace:
[...]
```
