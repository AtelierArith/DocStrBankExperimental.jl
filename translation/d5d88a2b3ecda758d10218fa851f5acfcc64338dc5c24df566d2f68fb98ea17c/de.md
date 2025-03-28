```
>>(B::BitVector, n) -> BitVector
```

Rechter Bitverschiebungsoperator, `B >> n`. Für `n >= 0` ist das Ergebnis `B` mit Elementen, die um `n` Positionen nach vorne verschoben werden, wobei mit `false`-Werten aufgefüllt wird. Wenn `n < 0` ist, werden die Elemente nach hinten verschoben. Entspricht `B << -n`.

# Beispiele

```jldoctest
julia> B = BitVector([true, false, true, false, false])
5-element BitVector:
 1
 0
 1
 0
 0

julia> B >> 1
5-element BitVector:
 0
 1
 0
 1
 0

julia> B >> -1
5-element BitVector:
 0
 1
 0
 0
 0
```
