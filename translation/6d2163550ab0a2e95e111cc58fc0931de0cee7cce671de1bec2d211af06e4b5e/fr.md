```
Vararg{T,N}
```

Le dernier paramètre d'un type de tuple [`Tuple`](@ref) peut être la valeur spéciale `Vararg`, qui désigne un nombre quelconque d'éléments en fin de liste. `Vararg{T,N}` correspond exactement à `N` éléments de type `T`. Enfin, `Vararg{T}` correspond à zéro ou plusieurs éléments de type `T`. Les types de tuple `Vararg` sont utilisés pour représenter les arguments acceptés par les méthodes varargs (voir la section sur [Fonctions Varargs](@ref) dans le manuel.)

Voir aussi [`NTuple`](@ref).

# Exemples

```jldoctest
julia> mytupletype = Tuple{AbstractString, Vararg{Int}}
Tuple{AbstractString, Vararg{Int64}}

julia> isa(("1",), mytupletype)
true

julia> isa(("1",1), mytupletype)
true

julia> isa(("1",1,2), mytupletype)
true

julia> isa(("1",1,2,3.0), mytupletype)
false
```
