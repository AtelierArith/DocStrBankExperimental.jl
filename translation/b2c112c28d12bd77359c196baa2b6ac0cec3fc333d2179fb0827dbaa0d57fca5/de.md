```
prod(itr; [init])
```

Gibt das Produkt aller Elemente einer Sammlung zurück.

Der Rückgabewert ist `Int` für vorzeichenbehaftete Ganzzahlen, die kleiner als die Systemwortgröße sind, und `UInt` für vorzeichenlose Ganzzahlen, die kleiner als die Systemwortgröße sind. Für alle anderen Argumente wird ein gemeinsamer Rückgabewert gefunden, zu dem alle Argumente befördert werden.

Der Wert, der für leere `itr` zurückgegeben wird, kann durch `init` angegeben werden. Es muss die multiplikative Identität (d.h. eins) sein, da nicht spezifiziert ist, ob `init` für nicht leere Sammlungen verwendet wird.

!!! compat "Julia 1.6"
    Das Schlüsselwort-Argument `init` erfordert Julia 1.6 oder höher.


Siehe auch: [`reduce`](@ref), [`cumprod`](@ref), [`any`](@ref).

# Beispiele

```jldoctest
julia> prod(1:5)
120

julia> prod(1:5; init = 1.0)
120.0
```
