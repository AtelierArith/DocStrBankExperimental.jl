```
in(item, collection) -> Bool
∈(item, collection) -> Bool
```

Déterminez si un élément est dans la collection donnée, dans le sens où il est [`==`](@ref) à l'une des valeurs générées en itérant sur la collection. Retournez une valeur `Bool`, sauf si `item` est [`missing`](@ref) ou si `collection` contient `missing` mais pas `item`, auquel cas `missing` est retourné ([logique à trois valeurs](https://en.wikipedia.org/wiki/Three-valued_logic), correspondant au comportement de [`any`](@ref) et [`==`](@ref)).

Certaines collections suivent une définition légèrement différente. Par exemple, les [`Set`](@ref)s vérifient si l'élément est [`isequal`](@ref) à l'un des éléments ; les [`Dict`](@ref)s recherchent des paires `key=>value`, et la `key` est comparée en utilisant [`isequal`](@ref).

Pour tester la présence d'une clé dans un dictionnaire, utilisez [`haskey`](@ref) ou `k in keys(dict)`. Pour les collections mentionnées ci-dessus, le résultat est toujours un `Bool`.

Lors de la diffusion avec `in.(items, collection)` ou `items .∈ collection`, à la fois `item` et `collection` sont diffusés, ce qui n'est souvent pas ce qui est prévu. Par exemple, si les deux arguments sont des vecteurs (et que les dimensions correspondent), le résultat est un vecteur indiquant si chaque valeur dans la collection `items` est `in` la valeur à la position correspondante dans `collection`. Pour obtenir un vecteur indiquant si chaque valeur dans `items` est dans `collection`, enveloppez `collection` dans un tuple ou un `Ref` comme ceci : `in.(items, Ref(collection))` ou `items .∈ Ref(collection)`.

Voir aussi : [`∉`](@ref), [`insorted`](@ref), [`contains`](@ref), [`occursin`](@ref), [`issubset`](@ref).

# Exemples

```jldoctest
julia> a = 1:3:20
1:3:19

julia> 4 in a
true

julia> 5 in a
false

julia> missing in [1, 2]
missing

julia> 1 in [2, missing]
missing

julia> 1 in [1, missing]
true

julia> missing in Set([1, 2])
false

julia> (1=>missing) in Dict(1=>10, 2=>20)
missing

julia> [1, 2] .∈ [2, 3]
2-element BitVector:
 0
 0

julia> [1, 2] .∈ ([2, 3],)
2-element BitVector:
 0
 1
```
