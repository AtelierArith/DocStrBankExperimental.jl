```
getindex(type[, elements...])
```

Konstruiere ein 1-d Array des angegebenen Typs. Dies wird normalerweise mit der Syntax `Type[]` aufgerufen. Elementwerte können mit `Type[a,b,c,...]` angegeben werden.

# Beispiele

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
