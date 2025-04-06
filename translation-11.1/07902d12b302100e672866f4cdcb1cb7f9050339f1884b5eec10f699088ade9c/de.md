```
findmin(itr) -> (x, index)
```

Gibt das minimale Element der Sammlung `itr` und seinen Index oder Schlüssel zurück. Wenn es mehrere minimale Elemente gibt, wird das erste zurückgegeben. `NaN` wird als kleiner als alle anderen Werte außer `missing` behandelt.

Die Indizes sind vom gleichen Typ wie die, die von [`keys(itr)`](@ref) und [`pairs(itr)`](@ref) zurückgegeben werden.

Siehe auch: [`findmax`](@ref), [`argmin`](@ref), [`minimum`](@ref).

# Beispiele

```jldoctest
julia> findmin([8, 0.1, -9, pi])
(-9.0, 3)

julia> findmin([1, 7, 7, 6])
(1, 1)

julia> findmin([1, 7, 7, NaN])
(NaN, 4)
```
