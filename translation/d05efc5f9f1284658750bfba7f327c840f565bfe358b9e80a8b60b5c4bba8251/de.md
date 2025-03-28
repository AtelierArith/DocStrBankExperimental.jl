```
argmin(itr)
```

Gibt den Index oder Schlüssel des minimalen Elements in einer Sammlung zurück. Wenn es mehrere minimale Elemente gibt, wird das erste zurückgegeben.

Die Sammlung darf nicht leer sein.

Die Indizes sind vom gleichen Typ wie die, die von [`keys(itr)`](@ref) und [`pairs(itr)`](@ref) zurückgegeben werden.

`NaN` wird als kleiner als alle anderen Werte außer `missing` behandelt.

Siehe auch: [`argmax`](@ref), [`findmin`](@ref).

# Beispiele

```jldoctest
julia> argmin([8, 0.1, -9, pi])
3

julia> argmin([7, 1, 1, 6])
2

julia> argmin([7, 1, 1, NaN])
4
```
