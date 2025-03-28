```
Iterators.filter(flt, itr)
```

Gegeben einer Prädikatsfunktion `flt` und einem iterierbaren Objekt `itr`, gibt diese Funktion ein iterierbares Objekt zurück, das bei der Iteration die Elemente `x` von `itr` liefert, die `flt(x)` erfüllen. Die Reihenfolge des ursprünglichen Iterators bleibt erhalten.

Diese Funktion ist *lazy*; das heißt, es ist garantiert, dass sie in $Θ(1)$ Zeit zurückgibt und $Θ(1)$ zusätzlichen Speicher verwendet, und `flt` wird nicht durch einen Aufruf von `filter` aufgerufen. Aufrufe an `flt` werden gemacht, wenn über das zurückgegebene iterierbare Objekt iteriert wird. Diese Aufrufe werden nicht zwischengespeichert und wiederholte Aufrufe werden gemacht, wenn erneut iteriert wird.

!!! warning
    Nachfolgende *lazy* Transformationen des von `filter` zurückgegebenen Iterators, wie sie von `Iterators.reverse` oder `cycle` durchgeführt werden, verzögern ebenfalls die Aufrufe an `flt`, bis das zurückgegebene iterierbare Objekt gesammelt oder durchlaufen wird. Wenn das Filterprädikat nichtdeterministisch ist oder seine Rückgabewerte von der Reihenfolge der Iteration über die Elemente von `itr` abhängen, kann die Zusammensetzung mit lazy Transformationen zu überraschendem Verhalten führen. Wenn dies unerwünscht ist, stellen Sie entweder sicher, dass `flt` eine reine Funktion ist, oder sammeln Sie zwischenzeitliche `filter`-Iteratoren, bevor Sie weitere Transformationen durchführen.


Siehe [`Base.filter`](@ref) für eine eager Implementierung des Filterns für Arrays.

# Beispiele

```jldoctest
julia> f = Iterators.filter(isodd, [1, 2, 3, 4, 5])
Base.Iterators.Filter{typeof(isodd), Vector{Int64}}(isodd, [1, 2, 3, 4, 5])

julia> foreach(println, f)
1
3
5

julia> [x for x in [1, 2, 3, 4, 5] if isodd(x)]  # sammelt einen Generator über Iterators.filter
3-element Vector{Int64}:
 1
 3
 5
```
