```
skipmissing(itr)
```

Renvoie un itérateur sur les éléments de `itr` en sautant les valeurs [`missing`](@ref). L'objet retourné peut être indexé en utilisant les indices de `itr` si ce dernier est indexable. Les indices correspondant aux valeurs manquantes ne sont pas valides : ils sont ignorés par [`keys`](@ref) et [`eachindex`](@ref), et une `MissingException` est levée lorsque vous essayez de les utiliser.

Utilisez [`collect`](@ref) pour obtenir un `Array` contenant les valeurs non-`missing` dans `itr`. Notez que même si `itr` est un tableau multidimensionnel, le résultat sera toujours un `Vector` car il n'est pas possible de supprimer les valeurs manquantes tout en préservant les dimensions de l'entrée.

Voir aussi [`coalesce`](@ref), [`ismissing`](@ref), [`something`](@ref).

# Exemples

```jldoctest
julia> x = skipmissing([1, missing, 2])
skipmissing(Union{Missing, Int64}[1, missing, 2])

julia> sum(x)
3

julia> x[1]
1

julia> x[2]
ERROR: MissingException: la valeur à l'index (2,) est manquante
[...]

julia> argmax(x)
3

julia> collect(keys(x))
Vector{Int64} de 2 éléments:
 1
 3

julia> collect(skipmissing([1, missing, 2]))
Vector{Int64} de 2 éléments:
 1
 2

julia> collect(skipmissing([1 missing; 2 missing]))
Vector{Int64} de 2 éléments:
 1
 2
```
