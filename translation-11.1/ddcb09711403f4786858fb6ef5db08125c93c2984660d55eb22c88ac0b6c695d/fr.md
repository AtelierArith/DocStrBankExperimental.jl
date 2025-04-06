```
subtypes(T::DataType)
```

Renvoie une liste des sous-types immédiats du type de données `T`. Notez que tous les sous-types actuellement chargés sont inclus, y compris ceux qui ne sont pas visibles dans le module actuel.

Voir aussi [`supertype`](@ref), [`supertypes`](@ref), [`methodswith`](@ref).

# Exemples

```jldoctest
julia> subtypes(Integer)
3-element Vector{Any}:
 Bool
 Signed
 Unsigned
```
