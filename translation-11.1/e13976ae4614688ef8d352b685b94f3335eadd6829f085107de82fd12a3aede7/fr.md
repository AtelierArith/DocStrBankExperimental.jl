```
oneunit(x::T)
oneunit(T::Type)
```

Retourne `T(one(x))`, où `T` est soit le type de l'argument soit (si un type est passé) l'argument. Cela diffère de [`one`](@ref) pour les quantités dimensionnelles : `one` est sans dimension (une identité multiplicative) tandis que `oneunit` est dimensionnelle (du même type que `x`, ou de type `T`).

# Exemples

```jldoctest
julia> oneunit(3.7)
1.0

julia> import Dates; oneunit(Dates.Day)
1 jour
```
