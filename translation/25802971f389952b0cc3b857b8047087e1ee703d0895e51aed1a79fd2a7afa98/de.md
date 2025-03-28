```
nonmissingtype(T::Type)
```

Wenn `T` eine Vereinigung von Typen ist, die `Missing` enthalten, gibt es einen neuen Typ zurück, bei dem `Missing` entfernt wurde.

# Beispiele

```jldoctest
julia> nonmissingtype(Union{Int64,Missing})
Int64

julia> nonmissingtype(Any)
Any
```

!!! compat "Julia 1.3"
    Diese Funktion ist seit Julia 1.3 exportiert.

