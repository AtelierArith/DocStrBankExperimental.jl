```
UnitRange{T<:Real}
```

Ein Bereich, der durch einen `start` und `stop` des Typs `T` parametrisiert ist, gefüllt mit Elementen, die um `1` von `start` bis `stop` verteilt sind, bis `stop` überschritten wird. Die Syntax `a:b` mit `a` und `b`, die beide `Integer` sind, erstellt einen `UnitRange`.

# Beispiele

```jldoctest
julia> collect(UnitRange(2.3, 5.2))
3-element Vector{Float64}:
 2.3
 3.3
 4.3

julia> typeof(1:10)
UnitRange{Int64}
```
