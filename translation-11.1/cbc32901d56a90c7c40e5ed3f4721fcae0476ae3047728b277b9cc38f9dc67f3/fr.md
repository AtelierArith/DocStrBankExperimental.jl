```
IdDict([itr])
```

`IdDict{K,V}()` construit une table de hachage en utilisant [`objectid`](@ref) comme hachage et `===` comme égalité avec des clés de type `K` et des valeurs de type `V`. Voir [`Dict`](@ref) pour plus d'aide et [`IdSet`](@ref) pour la version ensemble de cela.

Dans l'exemple ci-dessous, les clés de `Dict` sont toutes `isequal` et sont donc hachées de la même manière, elles sont donc écrasées. L'`IdDict` hache par identifiant d'objet, et préserve donc les 3 clés différentes.

# Exemples

```julia-repl
julia> Dict(true => "yes", 1 => "no", 1.0 => "maybe")
Dict{Real, String} with 1 entry:
  1.0 => "maybe"

julia> IdDict(true => "yes", 1 => "no", 1.0 => "maybe")
IdDict{Any, String} with 3 entries:
  true => "yes"
  1.0  => "maybe"
  1    => "no"
```
