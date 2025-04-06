```
propertynames(x, private=false)
```

Erhalten Sie ein Tupel oder einen Vektor der Eigenschaften (`x.property`) eines Objekts `x`. Dies ist typischerweise dasselbe wie [`fieldnames(typeof(x))`](@ref), aber Typen, die [`getproperty`](@ref) überladen, sollten im Allgemeinen auch `propertynames` überladen, um die Eigenschaften einer Instanz des Typs zu erhalten.

`propertynames(x)` kann nur "öffentliche" Eigenschaftsnamen zurückgeben, die Teil der dokumentierten Schnittstelle von `x` sind. Wenn Sie möchten, dass auch "private" Eigenschaftsnamen zurückgegeben werden, die für den internen Gebrauch bestimmt sind, übergeben Sie `true` als optionales zweites Argument. Die REPL-Tab-Vervollständigung bei `x.` zeigt nur die `private=false` Eigenschaften an.

Siehe auch: [`hasproperty`](@ref), [`hasfield`](@ref).
