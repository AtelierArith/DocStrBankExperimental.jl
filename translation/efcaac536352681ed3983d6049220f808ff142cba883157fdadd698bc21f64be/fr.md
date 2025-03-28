```
keytype(T::Type{<:AbstractArray})
keytype(A::AbstractArray)
```

Renvoie le type de clé d'un tableau. Cela est égal à l'[`eltype`](@ref) du résultat de `keys(...)`, et est fourni principalement pour la compatibilité avec l'interface de dictionnaire.

# Exemples

```jldoctest
julia> keytype([1, 2, 3]) == Int
true

julia> keytype([1 2; 3 4])
CartesianIndex{2}
```

!!! compat "Julia 1.2"
    Pour les tableaux, cette fonction nécessite au moins Julia 1.2.

