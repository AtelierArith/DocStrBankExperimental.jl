```
maximum(itr; [init])
```

Gibt das größte Element in einer Sammlung zurück.

Der zurückgegebene Wert für leeres `itr` kann durch `init` angegeben werden. Es muss ein neutrales Element für `max` sein (d.h. das kleiner oder gleich jedem anderen Element ist), da nicht spezifiziert ist, ob `init` für nicht-leere Sammlungen verwendet wird.

!!! compat "Julia 1.6"
    Das Schlüsselwort-Argument `init` erfordert Julia 1.6 oder später.


# Beispiele

```jldoctest
julia> maximum(-20.5:10)
9.5

julia> maximum([1,2,3])
3

julia> maximum(())
ERROR: ArgumentError: Reduzieren über eine leere Sammlung ist nicht erlaubt; ziehen Sie in Betracht, `init` an den Reducer zu übergeben
Stacktrace:
[...]

julia> maximum((); init=-Inf)
-Inf
```
