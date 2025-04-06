```
Base.summarysize(obj; exclude=Union{...}, chargeall=Union{...}) -> Int
```

Calcule la quantité de mémoire, en octets, utilisée par tous les objets uniques accessibles à partir de l'argument.

# Arguments Clés

  * `exclude` : spécifie les types d'objets à exclure de la traversée.
  * `chargeall` : spécifie les types d'objets pour lesquels il faut toujours prendre en compte la taille de tous leurs champs, même si ces champs seraient normalement exclus.

Voir aussi [`sizeof`](@ref).

# Exemples

```jldoctest
julia> Base.summarysize(1.0)
8

julia> Base.summarysize(Ref(rand(100)))
848

julia> sizeof(Ref(rand(100)))
8
```
