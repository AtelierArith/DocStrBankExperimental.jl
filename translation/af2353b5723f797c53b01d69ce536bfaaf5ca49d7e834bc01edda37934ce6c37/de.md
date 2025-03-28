```
maximum(f, itr; [init])
```

Gibt das größte Ergebnis zurück, das durch den Aufruf der Funktion `f` auf jedes Element von `itr` erzielt wird.

Der zurückgegebene Wert für ein leeres `itr` kann durch `init` festgelegt werden. Es muss ein neutrales Element für `max` sein (d.h. das kleiner oder gleich jedem anderen Element ist), da nicht spezifiziert ist, ob `init` für nicht leere Sammlungen verwendet wird.

!!! compat "Julia 1.6"
    Das Schlüsselwort-Argument `init` erfordert Julia 1.6 oder höher.


# Beispiele

```jldoctest
julia> maximum(length, ["Julion", "Julia", "Jule"])
6

julia> maximum(length, []; init=-1)
-1

julia> maximum(sin, Real[]; init=-1.0)  # gut, da die Ausgabe von sin >= -1 ist
-1.0
```
