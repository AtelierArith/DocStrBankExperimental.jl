```
unique!(f, A::AbstractVector)
```

Sélectionne une valeur de `A` pour chaque valeur unique produite par `f` appliqué aux éléments de `A`, puis retourne le `A` modifié.

!!! compat "Julia 1.1"
    Cette méthode est disponible depuis Julia 1.1.


# Exemples

```jldoctest
julia> unique!(x -> x^2, [1, -1, 3, -3, 4])
3-element Vector{Int64}:
 1
 3
 4

julia> unique!(n -> n%3, [5, 1, 8, 9, 3, 4, 10, 7, 2, 6])
3-element Vector{Int64}:
 5
 1
 9

julia> unique!(iseven, [2, 3, 5, 7, 9])
2-element Vector{Int64}:
 2
 3
```
