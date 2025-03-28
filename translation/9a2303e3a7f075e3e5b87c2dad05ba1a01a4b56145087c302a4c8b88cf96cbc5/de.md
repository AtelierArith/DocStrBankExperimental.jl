```
hash(x[, h::UInt]) -> UInt
```

Berechnet einen ganzzahligen Hash-Code, sodass `isequal(x,y)` impliziert, dass `hash(x)==hash(y)`. Das optionale zweite Argument `h` ist ein weiterer Hash-Code, der mit dem Ergebnis gemischt werden soll.

Neue Typen sollten die 2-Argument-Form implementieren, typischerweise indem sie die 2-Argument `hash`-Methode rekursiv aufrufen, um die Hashes der Inhalte miteinander (und mit `h`) zu mischen. Typischerweise sollte jeder Typ, der `hash` implementiert, auch seine eigene [`==`](@ref) (und damit [`isequal`](@ref)) implementieren, um die oben genannte Eigenschaft zu garantieren.

Der Hash-Wert kann sich ändern, wenn ein neuer Julia-Prozess gestartet wird.

```jldoctest
julia> a = hash(10)
0x95ea2955abd45275

julia> hash(10, a) # verwendet nur die Ausgabe einer anderen Hash-Funktion als zweites Argument
0xd42bad54a8575b16
```

Siehe auch: [`objectid`](@ref), [`Dict`](@ref), [`Set`](@ref).
