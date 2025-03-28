```
isone(x)
```

Retourne `true` si `x == one(x)`; si `x` est un tableau, cela vérifie si `x` est une matrice identité.

# Exemples

```jldoctest
julia> isone(1.0)
true

julia> isone([1 0; 0 2])
false

julia> isone([1 0; 0 true])
true
```
