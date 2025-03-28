```
===(x,y) -> Bool
≡(x,y) -> Bool
```

Bestimmen Sie, ob `x` und `y` identisch sind, im Sinne davon, dass kein Programm sie unterscheiden könnte. Zuerst werden die Typen von `x` und `y` verglichen. Wenn diese identisch sind, werden veränderliche Objekte nach Adresse im Speicher und unveränderliche Objekte (wie Zahlen) nach Inhalt auf Bit-Ebene verglichen. Diese Funktion wird manchmal "egal" genannt. Sie gibt immer einen `Bool`-Wert zurück.

# Beispiele

```jldoctest
julia> a = [1, 2]; b = [1, 2];

julia> a == b
true

julia> a === b
false

julia> a === a
true
```
