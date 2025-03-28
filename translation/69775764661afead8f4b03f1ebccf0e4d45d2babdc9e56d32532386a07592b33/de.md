```
minimum(f, itr; [init])
```

Gibt das kleinste Ergebnis zurück, das durch den Aufruf der Funktion `f` auf jedes Element von `itr` erzielt wird.

Der zurückgegebene Wert für ein leeres `itr` kann durch `init` festgelegt werden. Es muss ein neutrales Element für `min` sein (d.h. das größer oder gleich jedem anderen Element ist), da nicht spezifiziert ist, ob `init` für nicht leere Sammlungen verwendet wird.

!!! compat "Julia 1.6"
    Das Schlüsselwort-Argument `init` erfordert Julia 1.6 oder höher.


# Beispiele

```jldoctest
julia> minimum(length, ["Julion", "Julia", "Jule"])
4

julia> minimum(length, []; init=typemax(Int64))
9223372036854775807

julia> minimum(sin, Real[]; init=1.0)  # gut, da die Ausgabe von sin <= 1 ist
1.0
```
