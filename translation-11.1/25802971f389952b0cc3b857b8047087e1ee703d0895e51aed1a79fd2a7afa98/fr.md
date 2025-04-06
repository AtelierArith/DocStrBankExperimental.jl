```
nonmissingtype(T::Type)
```

Si `T` est une union de types contenant `Missing`, renvoie un nouveau type avec `Missing` supprimé.

# Exemples

```jldoctest
julia> nonmissingtype(Union{Int64,Missing})
Int64

julia> nonmissingtype(Any)
Any
```

!!! compat "Julia 1.3"
    Cette fonction est exportée depuis Julia 1.3.

