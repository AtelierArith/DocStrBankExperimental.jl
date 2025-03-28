```
===(x,y) -> Bool
≡(x,y) -> Bool
```

Déterminez si `x` et `y` sont identiques, dans le sens où aucun programme ne pourrait les distinguer. D'abord, les types de `x` et `y` sont comparés. Si ceux-ci sont identiques, les objets mutables sont comparés par adresse en mémoire et les objets immuables (comme les nombres) sont comparés par contenu au niveau des bits. Cette fonction est parfois appelée "égal". Elle retourne toujours une valeur `Bool`.

# Exemples

```jldoctest
julia> a = [1, 2]; b = [1, 2];

julia> a == b
true

julia> a === b
false

julia> a === a
true
```
