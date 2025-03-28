```
AbstractRange{T} <: AbstractVector{T}
```

Obertyp für lineare Bereiche mit Elementen des Typs `T`. [`UnitRange`](@ref), [`LinRange`](@ref) und andere Typen sind Untertypen davon.

Alle Untertypen müssen [`step`](@ref) definieren. Daher ist [`LogRange`](@ref Base.LogRange) kein Untertyp von `AbstractRange`.
