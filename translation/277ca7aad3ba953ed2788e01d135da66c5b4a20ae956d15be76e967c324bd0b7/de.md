```
float(x)
```

Konvertiere eine Zahl oder ein Array in einen Gleitkomma-Datentyp.

Siehe auch: [`complex`](@ref), [`oftype`](@ref), [`convert`](@ref).

# Beispiele

```jldoctest
julia> float(1:1000)
1.0:1.0:1000.0

julia> float(typemax(Int32))
2.147483647e9
```
