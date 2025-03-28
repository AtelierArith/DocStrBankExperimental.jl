```
findmax(f, domain) -> (f(x), index)
```

Gibt ein Paar aus einem Wert im Bildbereich (Ausgaben von `f`) und dem Index oder Schlüssel des entsprechenden Wertes im `domain` (Eingaben an `f`) zurück, sodass `f(x)` maximiert wird. Wenn es mehrere maximale Punkte gibt, wird der erste zurückgegeben.

`domain` muss ein nicht leeres iterierbares Objekt sein, das [`keys`](@ref) unterstützt. Indizes sind vom gleichen Typ wie die von [`keys(domain)`](@ref) zurückgegebenen.

Werte werden mit `isless` verglichen.

!!! compat "Julia 1.7"
    Diese Methode erfordert Julia 1.7 oder höher.


# Beispiele

```jldoctest
julia> findmax(identity, 5:9)
(9, 5)

julia> findmax(-, 1:10)
(-1, 1)

julia> findmax(first, [(1, :a), (3, :b), (3, :c)])
(3, 2)

julia> findmax(cos, 0:π/2:2π)
(1.0, 1)
```
