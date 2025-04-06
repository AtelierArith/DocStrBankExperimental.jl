```
NTuple{N, T}
```

Une manière compacte de représenter le type d'un tuple de longueur `N` où tous les éléments sont de type `T`.

# Exemples

```jldoctest
julia> isa((1, 2, 3, 4, 5, 6), NTuple{6, Int})
true
```

Voir aussi [`ntuple`](@ref).
