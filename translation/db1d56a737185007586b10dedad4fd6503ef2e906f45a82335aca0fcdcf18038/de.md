```
dot(x, y)
x ⋅ y
```

Berechne das Skalarprodukt zwischen zwei Vektoren. Bei komplexen Vektoren wird der erste Vektor konjugiert.

`dot` funktioniert auch mit beliebigen iterierbaren Objekten, einschließlich Arrays beliebiger Dimension, solange `dot` für die Elemente definiert ist.

`dot` ist semantisch äquivalent zu `sum(dot(vx,vy) for (vx,vy) in zip(x, y))`, mit der zusätzlichen Einschränkung, dass die Argumente die gleiche Länge haben müssen.

`x ⋅ y` (wobei `⋅` durch Tab-Vervollständigung von `\cdot` im REPL eingegeben werden kann) ist ein Synonym für `dot(x, y)`.

# Beispiele

```jldoctest
julia> dot([1; 1], [2; 3])
5

julia> dot([im; im], [1; 1])
0 - 2im

julia> dot(1:5, 2:6)
70

julia> x = fill(2., (5,5));

julia> y = fill(3., (5,5));

julia> dot(x, y)
150.0
```
