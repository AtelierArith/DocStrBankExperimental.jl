```
flatten(iter)
```

Gegeben einen Iterator, der Iteratoren erzeugt, gibt einen Iterator zurück, der die Elemente dieser Iteratoren erzeugt. Anders ausgedrückt, die Elemente des Argument-Iterators werden zusammengefügt.

# Beispiele

```jldoctest
julia> collect(Iterators.flatten((1:2, 8:9)))
4-element Vector{Int64}:
 1
 2
 8
 9

julia> [(x,y) for x in 0:1 for y in 'a':'c']  # sammelt Generatoren, die Iterators.flatten verwenden
6-element Vector{Tuple{Int64, Char}}:
 (0, 'a')
 (0, 'b')
 (0, 'c')
 (1, 'a')
 (1, 'b')
 (1, 'c')
```
