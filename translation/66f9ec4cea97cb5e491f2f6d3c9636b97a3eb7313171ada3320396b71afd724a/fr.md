```
valtype(T::Type{<:AbstractArray})
valtype(A::AbstractArray)
```

Retourne le type de valeur d'un tableau. Cela est identique à [`eltype`](@ref) et est fourni principalement pour la compatibilité avec l'interface de dictionnaire.

# Exemples

```jldoctest
julia> valtype(["one", "two", "three"])
String
```

!!! compat "Julia 1.2"
    Pour les tableaux, cette fonction nécessite au moins Julia 1.2.

