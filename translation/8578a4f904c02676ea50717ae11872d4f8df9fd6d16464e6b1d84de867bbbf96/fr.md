```
all(p, itr) -> Bool
```

Déterminez si le prédicat `p` renvoie `true` pour tous les éléments de `itr`, renvoyant `false` dès que le premier élément de `itr` pour lequel `p` renvoie `false` est rencontré (court-circuit). Pour court-circuiter sur `true`, utilisez [`any`](@ref).

Si l'entrée contient des valeurs [`missing`](@ref), renvoyez `missing` si toutes les valeurs non manquantes sont `true` (ou équivalemment, si l'entrée ne contient aucune valeur `false`), suivant la [logique à trois valeurs](https://en.wikipedia.org/wiki/Three-valued_logic).

# Exemples

```jldoctest
julia> all(i->(4<=i<=6), [4,5,6])
true

julia> all(i -> (println(i); i < 3), 1:10)
1
2
3
false

julia> all(i -> i > 0, [1, missing])
missing

julia> all(i -> i > 0, [-1, missing])
false

julia> all(i -> i > 0, [1, 2])
true
```
