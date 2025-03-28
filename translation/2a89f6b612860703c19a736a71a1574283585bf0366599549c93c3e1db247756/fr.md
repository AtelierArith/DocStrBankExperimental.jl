```
last(itr, n::Integer)
```

Obtenez les derniers `n` éléments de la collection itérable `itr`, ou moins d'éléments si `itr` n'est pas assez long.

!!! compat "Julia 1.6"
    Cette méthode nécessite au moins Julia 1.6.


# Exemples

```jldoctest
julia> last(["foo", "bar", "qux"], 2)
2-element Vector{String}:
 "bar"
 "qux"

julia> last(1:6, 10)
1:6

julia> last(Float64[], 1)
Float64[]
```
