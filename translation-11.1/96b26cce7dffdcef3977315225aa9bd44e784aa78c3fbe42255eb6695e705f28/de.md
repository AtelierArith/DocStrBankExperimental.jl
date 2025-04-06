```
if/elseif/else
```

`if`/`elseif`/`else` führt eine bedingte Auswertung durch, die es ermöglicht, Teile des Codes je nach Wert eines booleschen Ausdrucks auszuwerten oder nicht auszuwerten. Hier ist die Anatomie der `if`/`elseif`/`else`-Bedingungssyntax:

```julia
if x < y
    println("x ist kleiner als y")
elseif x > y
    println("x ist größer als y")
else
    println("x ist gleich y")
end
```

Wenn der Bedingungsausdruck `x < y` wahr ist, wird der entsprechende Block ausgewertet; andernfalls wird der Bedingungsausdruck `x > y` ausgewertet, und wenn dieser wahr ist, wird der entsprechende Block ausgewertet; wenn keiner der Ausdrücke wahr ist, wird der `else`-Block ausgewertet. Die `elseif`- und `else`-Blöcke sind optional, und es können so viele `elseif`-Blöcke verwendet werden, wie gewünscht.

Im Gegensatz zu einigen anderen Sprachen müssen Bedingungen vom Typ `Bool` sein. Es reicht nicht aus, wenn Bedingungen in `Bool` umwandelbar sind.

```jldoctest
julia> if 1 end
ERROR: TypeError: non-boolean (Int64) used in boolean context
```
