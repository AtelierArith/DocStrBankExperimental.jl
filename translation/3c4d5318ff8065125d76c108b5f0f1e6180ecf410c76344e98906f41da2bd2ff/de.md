```
argmax(itr)
```

Gibt den Index oder Schlüssel des maximalen Elements in einer Sammlung zurück. Wenn es mehrere maximale Elemente gibt, wird das erste zurückgegeben.

Die Sammlung darf nicht leer sein.

Die Indizes sind vom gleichen Typ wie die, die von [`keys(itr)`](@ref) und [`pairs(itr)`](@ref) zurückgegeben werden.

Werte werden mit `isless` verglichen.

Siehe auch: [`argmin`](@ref), [`findmax`](@ref).

# Beispiele

```jldoctest
julia> argmax([8, 0.1, -9, pi])
1

julia> argmax([1, 7, 7, 6])
2

julia> argmax([1, 7, 7, NaN])
4
```
