```
findmin(f, domain) -> (f(x), index)
```

Retourne une paire d'une valeur dans le codomaine (sorties de `f`) et l'indice ou la clé de la valeur correspondante dans le `domain` (entrées de `f`) telle que `f(x)` est minimisé. S'il y a plusieurs points minimaux, alors le premier sera retourné.

`domain` doit être un itérable non vide.

Les indices sont du même type que ceux retournés par [`keys(domain)`](@ref) et [`pairs(domain)`](@ref).

`NaN` est considéré comme inférieur à toutes les autres valeurs sauf `missing`.

!!! compat "Julia 1.7"
    Cette méthode nécessite Julia 1.7 ou une version ultérieure.


# Exemples

```jldoctest
julia> findmin(identity, 5:9)
(5, 1)

julia> findmin(-, 1:10)
(-10, 10)

julia> findmin(first, [(2, :a), (2, :b), (3, :c)])
(2, 1)

julia> findmin(cos, 0:π/2:2π)
(-1.0, 3)
```
