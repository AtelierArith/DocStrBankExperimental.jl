```
thisind(s::AbstractString, i::Integer) -> Int
```

Wenn `i` innerhalb der Grenzen von `s` liegt, gibt den Index des Beginns des Zeichens zurück, dessen Kodierungseinheit `i` Teil davon ist. Mit anderen Worten, wenn `i` der Beginn eines Zeichens ist, gib `i` zurück; wenn `i` nicht der Beginn eines Zeichens ist, spule zurück bis zum Beginn eines Zeichens und gib diesen Index zurück. Wenn `i` gleich 0 oder `ncodeunits(s)+1` ist, gib `i` zurück. In allen anderen Fällen wirf `BoundsError`.

# Beispiele

```jldoctest
julia> thisind("α", 0)
0

julia> thisind("α", 1)
1

julia> thisind("α", 2)
1

julia> thisind("α", 3)
3

julia> thisind("α", 4)
ERROR: BoundsError: attempt to access 2-codeunit String at index [4]
[...]

julia> thisind("α", -1)
ERROR: BoundsError: attempt to access 2-codeunit String at index [-1]
[...]
```
