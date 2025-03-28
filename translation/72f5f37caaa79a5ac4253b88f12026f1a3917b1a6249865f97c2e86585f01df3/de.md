```
StepRange{T, S} <: OrdinalRange{T, S}
```

Bereiche mit Elementen des Typs `T` mit Abständen des Typs `S`. Der Schritt zwischen jedem Element ist konstant, und der Bereich wird in Bezug auf einen `start` und `stop` des Typs `T` und einen `step` des Typs `S` definiert. Weder `T` noch `S` sollten Fließkommatypen sein. Die Syntax `a:b:c` mit `b != 0` und `a`, `b` und `c`, die alle Ganzzahlen sind, erstellt einen `StepRange`.

# Beispiele

```jldoctest
julia> collect(StepRange(1, Int8(2), 10))
5-element Vector{Int64}:
 1
 3
 5
 7
 9

julia> typeof(StepRange(1, Int8(2), 10))
StepRange{Int64, Int8}

julia> typeof(1:3:6)
StepRange{Int64, Int64}
```
