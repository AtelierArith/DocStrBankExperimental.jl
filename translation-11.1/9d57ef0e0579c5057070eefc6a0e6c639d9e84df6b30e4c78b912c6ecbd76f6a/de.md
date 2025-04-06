```
OrdinalRange{T, S} <: AbstractRange{T}
```

Supertyp für ordinale Bereiche mit Elementen des Typs `T` und Abständen des Typs `S`. Die Schritte sollten immer exakte Vielfache von [`oneunit`](@ref) sein, und `T` sollte ein "diskreter" Typ sein, der keine Werte kleiner als `oneunit` haben kann. Zum Beispiel würden `Integer` oder `Date` Typen qualifizieren, während `Float64` dies nicht tun würde (da dieser Typ Werte kleiner als `oneunit(Float64)` darstellen kann). [`UnitRange`](@ref), [`StepRange`](@ref) und andere Typen sind Untertypen davon.
