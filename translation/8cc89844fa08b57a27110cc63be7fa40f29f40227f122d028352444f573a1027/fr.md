```
hasmethod(f, t::Type{<:Tuple}[, kwnames]; world=get_world_counter()) -> Bool
```

Déterminez si la fonction générique donnée a une méthode correspondant au `Tuple` des types d'arguments donnés avec la limite supérieure de l'âge du monde donnée par `world`.

Si un tuple de noms d'arguments de mot-clé `kwnames` est fourni, cela vérifie également si la méthode de `f` correspondant à `t` a les noms d'arguments de mot-clé donnés. Si la méthode correspondante accepte un nombre variable d'arguments de mot-clé, par exemple avec `kwargs...`, tous les noms donnés dans `kwnames` sont considérés comme valides. Sinon, les noms fournis doivent être un sous-ensemble des arguments de mot-clé de la méthode.

Voir aussi [`applicable`](@ref).

!!! compat "Julia 1.2"
    Fournir des noms d'arguments de mot-clé nécessite Julia 1.2 ou une version ultérieure.


# Exemples

```jldoctest
julia> hasmethod(length, Tuple{Array})
true

julia> f(; oranges=0) = oranges;

julia> hasmethod(f, Tuple{}, (:oranges,))
true

julia> hasmethod(f, Tuple{}, (:apples, :bananas))
false

julia> g(; xs...) = 4;

julia> hasmethod(g, Tuple{}, (:a, :b, :c, :d))  # g accepte des kwargs arbitraires
true
```
