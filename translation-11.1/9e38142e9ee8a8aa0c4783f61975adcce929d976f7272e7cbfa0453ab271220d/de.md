```
nand(x, y)
⊼(x, y)
```

Bitweises nand (nicht und) von `x` und `y`. Implementiert [dreiwertige Logik](https://de.wikipedia.org/wiki/Dreiwertige_Logik), gibt [`missing`](@ref) zurück, wenn eines der Argumente `missing` ist.

Die Infix-Operation `a ⊼ b` ist ein Synonym für `nand(a,b)`, und `⊼` kann durch Tab-Vervollständigung von `\nand` oder `\barwedge` in der Julia REPL eingegeben werden.

# Beispiele

```jldoctest
julia> nand(true, false)
true

julia> nand(true, true)
false

julia> nand(true, missing)
missing

julia> false ⊼ false
true

julia> [true; true; false] .⊼ [true; false; false]
3-element BitVector:
 0
 1
 1
```
