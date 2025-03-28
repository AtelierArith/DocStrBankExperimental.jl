```
getindex(type[, elements...])
```

Construit un tableau 1-d du type spécifié. Cela s'appelle généralement avec la syntaxe `Type[]`. Les valeurs des éléments peuvent être spécifiées en utilisant `Type[a,b,c,...]`.

# Exemples

```jldoctest
julia> Int8[1, 2, 3]
3-element Vector{Int8}:
 1
 2
 3

julia> getindex(Int8, 1, 2, 3)
3-element Vector{Int8}:
 1
 2
 3
```
