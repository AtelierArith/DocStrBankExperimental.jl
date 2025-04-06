```
unique!(A::AbstractVector)
```

Supprime les éléments en double tels que déterminés par [`isequal`](@ref) et [`hash`](@ref), puis retourne le `A` modifié. `unique!` retournera les éléments de `A` dans l'ordre dans lequel ils apparaissent. Si vous ne vous souciez pas de l'ordre des données retournées, alors appeler `(sort!(A); unique!(A))` sera beaucoup plus efficace tant que les éléments de `A` peuvent être triés.

# Exemples

```jldoctest
julia> unique!([1, 1, 1])
1-element Vector{Int64}:
 1

julia> A = [7, 3, 2, 3, 7, 5];

julia> unique!(A)
4-element Vector{Int64}:
 7
 3
 2
 5

julia> B = [7, 6, 42, 6, 7, 42];

julia> sort!(B);  # unique! peut traiter les données triées de manière beaucoup plus efficace.

julia> unique!(B)
3-element Vector{Int64}:
  6
  7
 42
```
