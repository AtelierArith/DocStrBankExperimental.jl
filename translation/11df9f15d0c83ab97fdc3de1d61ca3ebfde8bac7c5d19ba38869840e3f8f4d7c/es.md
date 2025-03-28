```
NTuple{N, T}
```

Una forma compacta de representar el tipo para una tupla de longitud `N` donde todos los elementos son del tipo `T`.

# Ejemplos

```jldoctest
julia> isa((1, 2, 3, 4, 5, 6), NTuple{6, Int})
true
```

Ver también [`ntuple`](@ref).
