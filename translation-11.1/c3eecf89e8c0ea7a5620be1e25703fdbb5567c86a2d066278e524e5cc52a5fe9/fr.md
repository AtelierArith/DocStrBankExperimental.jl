```
any(p, itr) -> Bool
```

Déterminez si le prédicat `p` renvoie `true` pour des éléments de `itr`, renvoyant `true` dès que le premier élément de `itr` pour lequel `p` renvoie `true` est rencontré (court-circuit). Pour court-circuiter sur `false`, utilisez [`all`](@ref).

Si l'entrée contient des valeurs [`missing`](@ref), renvoyez `missing` si toutes les valeurs non manquantes sont `false` (ou équivalemment, si l'entrée ne contient aucune valeur `true`), suivant la [logique à trois valeurs](https://en.wikipedia.org/wiki/Three-valued_logic).

# Exemples

```jldoctest
julia> any(i->(4<=i<=6), [3,5,7])
true

julia> any(i -> (println(i); i > 3), 1:10)
1
2
3
4
true

julia> any(i -> i > 0, [1, missing])
true

julia> any(i -> i > 0, [-1, missing])
missing

julia> any(i -> i > 0, [-1, 0])
false
```
