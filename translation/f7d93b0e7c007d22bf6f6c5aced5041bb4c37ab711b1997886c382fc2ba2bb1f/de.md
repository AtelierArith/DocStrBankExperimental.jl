```
nextind(str::AbstractString, i::Integer, n::Integer=1) -> Int
```

  * Fall `n == 1`

    Wenn `i` im Bereich von `s` liegt, gibt den Index des Beginns des Zeichens zurück, dessen Kodierung nach dem Index `i` beginnt. Mit anderen Worten, wenn `i` der Beginn eines Zeichens ist, gibt den Beginn des nächsten Zeichens zurück; wenn `i` nicht der Beginn eines Zeichens ist, gehe vorwärts, bis der Beginn eines Zeichens erreicht ist, und gib diesen Index zurück. Wenn `i` gleich `0` ist, gib `1` zurück. Wenn `i` im Bereich liegt, aber größer oder gleich `lastindex(str)` ist, gib `ncodeunits(str)+1` zurück. Andernfalls wird `BoundsError` ausgelöst.
  * Fall `n > 1`

    Verhält sich wie die Anwendung von `n`-mal `nextind` für `n==1`. Der einzige Unterschied ist, dass, wenn `n` so groß ist, dass die Anwendung von `nextind` `ncodeunits(str)+1` erreichen würde, jede verbleibende Iteration den zurückgegebenen Wert um `1` erhöht. Das bedeutet, dass in diesem Fall `nextind` einen Wert größer als `ncodeunits(str)+1` zurückgeben kann.
  * Fall `n == 0`

    Gib `i` nur zurück, wenn `i` ein gültiger Index in `s` ist oder gleich `0` ist. Andernfalls wird `StringIndexError` oder `BoundsError` ausgelöst.

# Beispiele

```jldoctest
julia> nextind("α", 0)
1

julia> nextind("α", 1)
3

julia> nextind("α", 3)
ERROR: BoundsError: attempt to access 2-codeunit String at index [3]
[...]

julia> nextind("α", 0, 2)
3

julia> nextind("α", 1, 2)
4
```
