```
any(itr) -> Bool
```

Testez si des éléments d'une collection booléenne sont `true`, retournant `true` dès que la première valeur `true` dans `itr` est rencontrée (court-circuit). Pour court-circuiter sur `false`, utilisez [`all`](@ref).

Si l'entrée contient des valeurs [`missing`](@ref), retournez `missing` si toutes les valeurs non manquantes sont `false` (ou équivalemment, si l'entrée ne contient aucune valeur `true`), suivant la [logique à trois valeurs](https://en.wikipedia.org/wiki/Three-valued_logic).

Voir aussi : [`all`](@ref), [`count`](@ref), [`sum`](@ref), [`|`](@ref), , [`||`](@ref).

# Exemples

```jldoctest
julia> a = [true,false,false,true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> any(a)
true

julia> any((println(i); v) for (i, v) in enumerate(a))
1
true

julia> any([missing, true])
true

julia> any([false, missing])
missing
```
