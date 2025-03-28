```
length(A::AbstractArray)
```

Retourne le nombre d'éléments dans le tableau, par défaut `prod(size(A))`.

# Exemples

```jldoctest
julia> length([1, 2, 3, 4])
4

julia> length([1 2; 3 4])
4
```
