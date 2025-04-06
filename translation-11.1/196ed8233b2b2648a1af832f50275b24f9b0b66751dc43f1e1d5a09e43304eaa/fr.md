```
typejoin(T, S, ...)
```

Renvoie l'ancêtre commun le plus proche des types `T` et `S`, c'est-à-dire le type le plus étroit dont ils héritent tous les deux. Récursive sur des varargs supplémentaires.

# Exemples

```jldoctest
julia> typejoin(Int, Float64)
Real

julia> typejoin(Int, Float64, ComplexF32)
Number
```
