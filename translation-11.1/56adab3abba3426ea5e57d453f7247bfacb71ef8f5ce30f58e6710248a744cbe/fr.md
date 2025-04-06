```
findnext(ch::AbstractChar, string::AbstractString, start::Integer)
```

Trouver la prochaine occurrence du caractère `ch` dans `string` en commençant à la position `start`.

!!! compat "Julia 1.3"
    Cette méthode nécessite au moins Julia 1.3.


# Exemples

```jldoctest
julia> findnext('z', "Hello to the world", 1) === nothing
true

julia> findnext('o', "Hello to the world", 6)
8
```
