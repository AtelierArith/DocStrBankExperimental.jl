```
all(itr) -> Bool
```

Testez si tous les éléments d'une collection booléenne sont `true`, retournant `false` dès que la première valeur `false` dans `itr` est rencontrée (court-circuit). Pour court-circuiter sur `true`, utilisez [`any`](@ref).

Si l'entrée contient des valeurs [`missing`](@ref), retournez `missing` si toutes les valeurs non manquantes sont `true` (ou équivalemment, si l'entrée ne contient aucune valeur `false`), suivant la [logique à trois valeurs](https://en.wikipedia.org/wiki/Three-valued_logic).

Voir aussi : [`all!`](@ref), [`any`](@ref), [`count`](@ref), [`&`](@ref), , [`&&`](@ref), [`allunique`](@ref).

# Exemples

```jldoctest
julia> a = [true,false,false,true]
4-element Vector{Bool}:
 1
 0
 0
 1

julia> all(a)
false

julia> all((println(i); v) for (i, v) in enumerate(a))
1
2
false

julia> all([missing, false])
false

julia> all([true, missing])
missing
```
