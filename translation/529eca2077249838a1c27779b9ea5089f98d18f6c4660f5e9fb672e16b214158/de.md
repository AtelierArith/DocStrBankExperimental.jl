```
xor(x, y)
⊻(x, y)
```

Bitweises exklusives Oder von `x` und `y`. Implementiert [dreiwertige Logik](https://de.wikipedia.org/wiki/Dreiwertige_Logik), gibt [`missing`](@ref) zurück, wenn eines der Argumente `missing` ist.

Die Infix-Operation `a ⊻ b` ist ein Synonym für `xor(a,b)`, und `⊻` kann durch Tab-Vervollständigung von `\xor` oder `\veebar` in der Julia REPL eingegeben werden.

# Beispiele

```jldoctest
julia> xor(true, false)
true

julia> xor(true, true)
false

julia> xor(true, missing)
missing

julia> false ⊻ false
false

julia> [true; true; false] .⊻ [true; false; false]
3-element BitVector:
 0
 1
 0
```
