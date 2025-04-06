```
findmax(f, domain) -> (f(x), index)
```

Retourne une paire d'une valeur dans le codomaine (sorties de `f`) et l'index ou la clé de la valeur correspondante dans le `domain` (entrées de `f`) telle que `f(x)` est maximisé. S'il y a plusieurs points maximaux, alors le premier sera retourné.

`domain` doit être un itérable non vide supportant [`keys`](@ref). Les indices sont du même type que ceux retournés par [`keys(domain)`](@ref).

Les valeurs sont comparées avec `isless`.

!!! compat "Julia 1.7"
    Cette méthode nécessite Julia 1.7 ou version ultérieure.


# Exemples

```jldoctest
julia> findmax(identity, 5:9)
(9, 5)

julia> findmax(-, 1:10)
(-1, 1)

julia> findmax(first, [(1, :a), (3, :b), (3, :c)])
(3, 2)

julia> findmax(cos, 0:π/2:2π)
(1.0, 1)
```
