```
sum(f, itr; [init])
```

Summiere die Ergebnisse des Aufrufs der Funktion `f` für jedes Element von `itr`.

Der Rückgabetyp ist `Int` für vorzeichenbehaftete Ganzzahlen, die kleiner als die Systemwortgröße sind, und `UInt` für vorzeichenlose Ganzzahlen, die kleiner als die Systemwortgröße sind. Für alle anderen Argumente wird ein gemeinsamer Rückgabetyp gefunden, zu dem alle Argumente befördert werden.

Der Wert, der für ein leeres `itr` zurückgegeben wird, kann durch `init` angegeben werden. Es muss die additive Identität (d.h. null) sein, da nicht spezifiziert ist, ob `init` für nicht leere Sammlungen verwendet wird.

!!! compat "Julia 1.6"
    Das Schlüsselwort-Argument `init` erfordert Julia 1.6 oder höher.


# Beispiele

```jldoctest
julia> sum(abs2, [2; 3; 4])
29
```

Beachte den wichtigen Unterschied zwischen `sum(A)` und `reduce(+, A)` für Arrays mit kleinem Ganzzahl-Elementtyp:

```jldoctest
julia> sum(Int8[100, 28])
128

julia> reduce(+, Int8[100, 28])
-128
```

Im ersteren Fall werden die Ganzzahlen auf die Systemwortgröße erweitert, und daher ist das Ergebnis 128. Im letzteren Fall findet keine solche Erweiterung statt, und der Überlauf der Ganzzahlen führt zu -128.
