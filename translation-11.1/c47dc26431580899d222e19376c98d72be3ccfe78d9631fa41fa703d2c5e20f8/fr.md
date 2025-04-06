```
first(itr, n::Integer)
```

Obtenez les premiers `n` éléments de la collection itérable `itr`, ou moins d'éléments si `itr` n'est pas assez long.

Voir aussi : [`startswith`](@ref), [`Iterators.take`](@ref).

!!! compat "Julia 1.6"
    Cette méthode nécessite au moins Julia 1.6.


# Exemples

```jldoctest
julia> first(["foo", "bar", "qux"], 2)
2-element Vector{String}:
 "foo"
 "bar"

julia> first(1:6, 10)
1:6

julia> first(Bool[], 1)
Bool[]
```
