```
unique(itr)
```

Renvoie un tableau contenant uniquement les éléments uniques de la collection `itr`, tels que déterminés par [`isequal`](@ref) et [`hash`](@ref), dans l'ordre où le premier de chaque ensemble d'éléments équivalents apparaît à l'origine. Le type d'élément de l'entrée est préservé.

Voir aussi : [`unique!`](@ref), [`allunique`](@ref), [`allequal`](@ref).

# Exemples

```jldoctest
julia> unique([1, 2, 6, 2])
3-element Vector{Int64}:
 1
 2
 6

julia> unique(Real[1, 1.0, 2])
2-element Vector{Real}:
 1
 2
```
