```
float(x)
```

Convertir un nombre ou un tableau en un type de données à virgule flottante.

Voir aussi : [`complex`](@ref), [`oftype`](@ref), [`convert`](@ref).

# Exemples

```jldoctest
julia> float(1:1000)
1.0:1.0:1000.0

julia> float(typemax(Int32))
2.147483647e9
```
