```
nor(x, y)
⊽(x, y)
```

Bitweises nor (nicht oder) von `x` und `y`. Implementiert [dreiwertige Logik](https://de.wikipedia.org/wiki/Dreiwertige_Logik), gibt [`missing`](@ref) zurück, wenn eines der Argumente `missing` ist und das andere nicht `true`.

Die Infix-Operation `a ⊽ b` ist ein Synonym für `nor(a,b)`, und `⊽` kann durch Tab-Vervollständigung von `\nor` oder `\barvee` in der Julia REPL eingegeben werden.

# Beispiele

```jldoctest
julia> nor(true, false)
false

julia> nor(true, true)
false

julia> nor(true, missing)
false

julia> false ⊽ false
true

julia> false ⊽ missing
missing

julia> [true; true; false] .⊽ [true; false; false]
3-element BitVector:
 0
 0
 1
```
