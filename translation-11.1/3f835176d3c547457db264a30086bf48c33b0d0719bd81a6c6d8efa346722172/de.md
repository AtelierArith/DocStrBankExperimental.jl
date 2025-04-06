```
prod(f, itr; [init])
```

Gibt das Produkt von `f` zurück, das auf jedes Element von `itr` angewendet wird.

Der Rückgabewert ist `Int` für vorzeichenbehaftete Ganzzahlen, die kleiner als die Systemwortgröße sind, und `UInt` für vorzeichenlose Ganzzahlen, die kleiner als die Systemwortgröße sind. Für alle anderen Argumente wird ein gemeinsamer Rückgabewert gefunden, zu dem alle Argumente befördert werden.

Der Wert, der für leeres `itr` zurückgegeben wird, kann durch `init` angegeben werden. Es muss die multiplikative Identität (d.h. eins) sein, da nicht spezifiziert ist, ob `init` für nicht leere Sammlungen verwendet wird.

!!! compat "Julia 1.6"
    Das Schlüsselwort-Argument `init` erfordert Julia 1.6 oder höher.


# Beispiele

```jldoctest
julia> prod(abs2, [2; 3; 4])
576
```
