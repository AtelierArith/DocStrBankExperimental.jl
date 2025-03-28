```
findmin(f, domain) -> (f(x), index)
```

Gibt ein Paar aus einem Wert im Wertebereich (Ausgaben von `f`) und dem Index oder Schlüssel des entsprechenden Wertes im `domain` (Eingaben an `f`) zurück, sodass `f(x)` minimiert wird. Wenn es mehrere minimale Punkte gibt, wird der erste zurückgegeben.

`domain` muss ein nicht leeres iterierbares Objekt sein.

Indizes sind vom gleichen Typ wie die von [`keys(domain)`](@ref) und [`pairs(domain)`](@ref) zurückgegebenen.

`NaN` wird als kleiner als alle anderen Werte außer `missing` behandelt.

!!! compat "Julia 1.7"
    Diese Methode erfordert Julia 1.7 oder höher.


# Beispiele

```jldoctest
julia> findmin(identity, 5:9)
(5, 1)

julia> findmin(-, 1:10)
(-10, 10)

julia> findmin(first, [(2, :a), (2, :b), (3, :c)])
(2, 1)

julia> findmin(cos, 0:π/2:2π)
(-1.0, 3)
```
