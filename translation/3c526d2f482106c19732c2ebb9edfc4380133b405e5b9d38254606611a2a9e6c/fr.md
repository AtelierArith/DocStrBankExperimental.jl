```
get(collection, key, default)
```

Retourne la valeur stockée pour la clé donnée, ou la valeur par défaut donnée si aucune correspondance pour la clé n'est présente.

!!! compat "Julia 1.7"
    Pour les tuples et les nombres, cette fonction nécessite au moins Julia 1.7.


# Exemples

```jldoctest
julia> d = Dict("a"=>1, "b"=>2);

julia> get(d, "a", 3)
1

julia> get(d, "c", 3)
3
```
