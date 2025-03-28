```
prevind(str::AbstractString, i::Integer, n::Integer=1) -> Int
```

  * Fall `n == 1`

    Wenn `i` im Bereich von `s` liegt, gibt den Index des Beginns des Zeichens zurück, dessen Kodierung vor dem Index `i` beginnt. Mit anderen Worten, wenn `i` der Beginn eines Zeichens ist, gibt den Beginn des vorherigen Zeichens zurück; wenn `i` nicht der Beginn eines Zeichens ist, spule bis zum Beginn eines Zeichens zurück und gib diesen Index zurück. Wenn `i` gleich `1` ist, gib `0` zurück. Wenn `i` gleich `ncodeunits(str)+1` ist, gib `lastindex(str)` zurück. Andernfalls wird `BoundsError` ausgelöst.
  * Fall `n > 1`

    Verhält sich wie die Anwendung von `n` Mal `prevind` für `n==1`. Der einzige Unterschied ist, dass, wenn `n` so groß ist, dass die Anwendung von `prevind` `0` erreichen würde, jede verbleibende Iteration den zurückgegebenen Wert um `1` verringert. Das bedeutet, dass in diesem Fall `prevind` einen negativen Wert zurückgeben kann.
  * Fall `n == 0`

    Gib `i` nur zurück, wenn `i` ein gültiger Index in `str` ist oder gleich `ncodeunits(str)+1` ist. Andernfalls wird `StringIndexError` oder `BoundsError` ausgelöst.

# Beispiele

```jldoctest
julia> prevind("α", 3)
1

julia> prevind("α", 1)
0

julia> prevind("α", 0)
ERROR: BoundsError: attempt to access 2-codeunit String at index [0]
[...]

julia> prevind("α", 2, 2)
0

julia> prevind("α", 2, 3)
-1
```
