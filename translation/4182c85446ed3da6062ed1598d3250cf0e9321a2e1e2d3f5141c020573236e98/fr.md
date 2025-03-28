```
IdSet{T}([itr])
IdSet()
```

IdSet{T}() construit un ensemble (voir [`Set`](@ref)) en utilisant `===` comme égalité avec des valeurs de type `T`.

Dans l'exemple ci-dessous, les valeurs sont toutes `isequal` donc elles sont écrasées dans l'ordinaire `Set`. L'`IdSet` compare par `===` et préserve donc les 3 valeurs différentes.

# Exemples

```jldoctest; filter = r"\n\s*(1|1\.0|true)"
julia> Set(Any[true, 1, 1.0])
Set{Any} avec 1 élément :
  1.0

julia> IdSet{Any}(Any[true, 1, 1.0])
IdSet{Any} avec 3 éléments :
  1.0
  1
  true
```
