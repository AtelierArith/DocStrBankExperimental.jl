```
minimum(itr; [init])
```

Gibt das kleinste Element in einer Sammlung zurück.

Der zurückgegebene Wert für leeres `itr` kann durch `init` angegeben werden. Es muss ein neutrales Element für `min` sein (d.h. das größer oder gleich jedem anderen Element ist), da nicht spezifiziert ist, ob `init` für nicht-leere Sammlungen verwendet wird.

!!! compat "Julia 1.6"
    Das Schlüsselwort-Argument `init` erfordert Julia 1.6 oder höher.


# Beispiele

```jldoctest
julia> minimum(-20.5:10)
-20.5

julia> minimum([1,2,3])
1

julia> minimum([])
ERROR: ArgumentError: Reduzieren über eine leere Sammlung ist nicht erlaubt; ziehen Sie in Betracht, `init` an den Reducer zu übergeben
Stacktrace:
[...]

julia> minimum([]; init=Inf)
Inf
```
