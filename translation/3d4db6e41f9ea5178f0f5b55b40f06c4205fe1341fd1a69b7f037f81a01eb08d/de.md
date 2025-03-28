```
count([f=identity,] itr; init=0) -> Integer
```

Zähle die Anzahl der Elemente in `itr`, für die die Funktion `f` `true` zurückgibt. Wenn `f` weggelassen wird, zähle die Anzahl der `true`-Elemente in `itr` (das sollte eine Sammlung von booleschen Werten sein). `init` gibt optional den Wert an, von dem aus gezählt werden soll, und bestimmt somit auch den Ausgabetyp.

!!! compat "Julia 1.6"
    Das `init`-Schlüsselwort wurde in Julia 1.6 hinzugefügt.


Siehe auch: [`any`](@ref), [`sum`](@ref).

# Beispiele

```jldoctest
julia> count(i->(4<=i<=6), [2,3,4,5,6])
3

julia> count([true, false, true, true])
3

julia> count(>(3), 1:7, init=0x03)
0x07
```
