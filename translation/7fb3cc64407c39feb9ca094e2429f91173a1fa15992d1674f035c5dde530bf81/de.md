```
findmax(itr) -> (x, index)
```

Gibt das maximale Element der Sammlung `itr` und seinen Index oder Schlüssel zurück. Wenn es mehrere maximale Elemente gibt, wird das erste zurückgegeben. Werte werden mit `isless` verglichen.

Indizes sind vom gleichen Typ wie die, die von [`keys(itr)`](@ref) und [`pairs(itr)`](@ref) zurückgegeben werden.

Siehe auch: [`findmin`](@ref), [`argmax`](@ref), [`maximum`](@ref).

# Beispiele

```jldoctest
julia> findmax([8, 0.1, -9, pi])
(8.0, 1)

julia> findmax([1, 7, 7, 6])
(7, 2)

julia> findmax([1, 7, 7, NaN])
(NaN, 4)
```
