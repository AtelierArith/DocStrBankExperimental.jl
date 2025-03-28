```
sum(itr; [init])
```

Gibt die Summe aller Elemente in einer Sammlung zurück.

Der Rückgabetyp ist `Int` für vorzeichenbehaftete Ganzzahlen, die kleiner als die Systemwortgröße sind, und `UInt` für vorzeichenlose Ganzzahlen, die kleiner als die Systemwortgröße sind. Für alle anderen Argumente wird ein gemeinsamer Rückgabetyp gefunden, zu dem alle Argumente befördert werden.

Der Wert, der für leeres `itr` zurückgegeben wird, kann durch `init` angegeben werden. Es muss die additive Identität (d.h. null) sein, da nicht spezifiziert ist, ob `init` für nicht leere Sammlungen verwendet wird.

!!! compat "Julia 1.6"
    Das Schlüsselwort-Argument `init` erfordert Julia 1.6 oder höher.


Siehe auch: [`reduce`](@ref), [`mapreduce`](@ref), [`count`](@ref), [`union`](@ref).

# Beispiele

```jldoctest
julia> sum(1:20)
210

julia> sum(1:20; init = 0.0)
210.0
```
