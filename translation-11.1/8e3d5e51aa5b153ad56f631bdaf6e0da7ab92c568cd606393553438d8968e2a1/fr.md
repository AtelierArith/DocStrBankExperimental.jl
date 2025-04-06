```
popat!(a::Vector, i::Integer, [default])
```

Supprime l'élément à l'index `i` donné et le retourne. Les éléments suivants sont décalés pour combler le vide résultant. Lorsque `i` n'est pas un index valide pour `a`, retourne `default`, ou lance une erreur si `default` n'est pas spécifié.

Voir aussi : [`pop!`](@ref), [`popfirst!`](@ref), [`deleteat!`](@ref), [`splice!`](@ref).

!!! compat "Julia 1.5"
    Cette fonction est disponible depuis Julia 1.5.


# Exemples

```jldoctest
julia> a = [4, 3, 2, 1]; popat!(a, 2)
3

julia> a
3-element Vector{Int64}:
 4
 2
 1

julia> popat!(a, 4, missing)
missing

julia> popat!(a, 4)
ERROR: BoundsError: attempt to access 3-element Vector{Int64} at index [4]
[...]
```
