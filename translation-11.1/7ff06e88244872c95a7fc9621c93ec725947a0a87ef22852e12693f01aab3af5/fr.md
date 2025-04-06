```
findlast(ch::AbstractChar, string::AbstractString)
```

Trouver la dernière occurrence du caractère `ch` dans `string`.

!!! compat "Julia 1.3"
    Cette méthode nécessite au moins Julia 1.3.


# Exemples

```jldoctest
julia> findlast('p', "happy")
4

julia> findlast('z', "happy") === nothing
true
```
