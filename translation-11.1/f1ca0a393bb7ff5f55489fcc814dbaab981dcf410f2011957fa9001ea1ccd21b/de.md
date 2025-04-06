```
extrema(itr; [init]) -> (mn, mx)
```

Berechne sowohl das Minimum `mn` als auch das Maximum `mx` Element in einem einzigen Durchgang und gebe sie als 2-Tupel zurück.

Der zurückgegebene Wert für leeres `itr` kann durch `init` festgelegt werden. Es muss ein 2-Tupel sein, dessen erstes und zweites Element neutrale Elemente für `min` und `max` sind (d.h. die größer/kleiner oder gleich jedem anderen Element sind). Folglich wird das zurückgegebene `(mn, mx)` Tupel, wenn `itr` leer ist, die Bedingung `mn ≥ mx` erfüllen. Wenn `init` angegeben ist, kann es auch für nicht-leeres `itr` verwendet werden.

!!! compat "Julia 1.8"
    Das Schlüsselwort-Argument `init` erfordert Julia 1.8 oder höher.


# Beispiele

```jldoctest
julia> extrema(2:10)
(2, 10)

julia> extrema([9,pi,4.5])
(3.141592653589793, 9.0)

julia> extrema([]; init = (Inf, -Inf))
(Inf, -Inf)
```
