```
UnionAll
```

Une union de types sur toutes les valeurs d'un paramètre de type. `UnionAll` est utilisé pour décrire des types paramétriques où les valeurs de certains paramètres ne sont pas connues. Voir la section du manuel sur [UnionAll Types](@ref).

# Exemples

```jldoctest
julia> typeof(Vector)
UnionAll

julia> typeof(Vector{Int})
DataType
```
