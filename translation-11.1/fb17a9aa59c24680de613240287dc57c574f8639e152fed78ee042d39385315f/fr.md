```
∉(item, collection) -> Bool
∌(collection, item) -> Bool
```

Négation de `∈` et `∋`, c'est-à-dire vérifie que `item` n'est pas dans `collection`.

Lors de la diffusion avec `items .∉ collection`, à la fois `item` et `collection` sont diffusés, ce qui n'est souvent pas ce qui est voulu. Par exemple, si les deux arguments sont des vecteurs (et que les dimensions correspondent), le résultat est un vecteur indiquant si chaque valeur dans `collection items` n'est pas dans la valeur à la position correspondante dans `collection`. Pour obtenir un vecteur indiquant si chaque valeur dans `items` n'est pas dans `collection`, enveloppez `collection` dans un tuple ou un `Ref` comme ceci : `items .∉ Ref(collection)`.

# Exemples

```jldoctest
julia> 1 ∉ 2:4
true

julia> 1 ∉ 1:3
false

julia> [1, 2] .∉ [2, 3]
2-element BitVector:
 1
 1

julia> [1, 2] .∉ ([2, 3],)
2-element BitVector:
 1
 0
```
